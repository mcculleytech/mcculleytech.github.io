+++
title = "claude skills vs. claude.md"
date = "2026-04-13T00:00:00-05:00"
author = "alex mcculley"
cover = ""
coverCaption = ""
tags = ["ai", "claude"]
keywords = ["ai", "claude", "claude skills", "claude.md"]
description = "mistakes were made"
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
Toc = false
aiDisclaimer = true
+++

In one of my [previous blog posts](/posts/using-ai-to-manage-my-nix-configs/), I discussed using the `CLAUDE.md` file in order to have AI create services for my NixOS configuration in a more deterministic manner. And while that did work, it's technically not best practice. I needed to migrate away from the `CLAUDE.md` file into a skill that can be invoked either automatically or manually through a slash command, which was designed for repeatable processes.

The `CLAUDE.md` file is more for naming schemes, architectural decisions and verification tasks than repeatable processes. And while you can use it to document and inform the model of repeatable processes, it's better to leave those as skills files (or commands for simpler tasks, but that term is more legacy these days).

The good news is that the migration from the `CLAUDE.md` to skills is super easy. You can just tell Claude to translate certain sections of the `CLAUDE.md` into skills files and place them in the appropriate section of your repository, which is the `.claude/skills/<SKILL-NAME>/SKILL.md` directory in your repo. Below is an example of one I pulled out of [my nixos-config repo's](https://github.com/mcculleytech/nixos-config) `CLAUDE.md` — this one is a repeatable process for wiring a new service into Prometheus and Grafana, invoked as `/add-monitoring <service>`:

<details>
<summary>SKILL.md (click to expand)</summary>

````markdown
Add Prometheus monitoring and a Grafana dashboard for a service. The service to add monitoring for is: $ARGUMENTS

If no service name was provided in $ARGUMENTS, ask the user which service needs monitoring before proceeding.

---

## Step 1: Identify the Service

Confirm the service name and which host it runs on. Read the service's `.nix` file to understand its current configuration.

---

## Step 2: Determine the Monitoring Path

Choose one of the two paths:

**Path A — Service has a built-in Prometheus metrics endpoint**
(Examples: Traefik exposes metrics on port 8080, Blocky on port 4000)

1. Enable the metrics endpoint within the service's own config if not already enabled.
2. Ensure the metrics port is open in `networking.firewall.allowedTCPPorts` in the service's `.nix` file.
3. Skip to Step 3.

**Path B — Service needs a dedicated NixOS exporter**
(Examples: PostgreSQL → `services.prometheus.exporters.postgres`, nginx → `services.prometheus.exporters.nginx`)

1. Check available exporters at `https://search.nixos.org/options?channel=25.11&query=services.prometheus.exporters` to find the right one.
2. Enable the exporter in the service's `.nix` file:
   ```nix
   services.prometheus.exporters.<name> = {
     enable = true;
     port = <exporter-port>;
   };
   networking.firewall.allowedTCPPorts = [ <exporter-port> ];
   ```
3. Note the exporter port for Step 3.

---

## Step 3: Add a scrapeConfigs Entry

Edit `hosts/common/optional/roles/server/prometheus.nix` and add a new entry to the `scrapeConfigs` list.

Follow the existing pattern exactly — IPs must come from `hosts = config.lab.hosts` (never hardcoded):

```nix
{
  job_name = "<service-name>";
  static_configs = [
    {
      targets = [ "${hosts.<hostname>.ip}:<port>" ];
    }
  ];
}
```

---

## Step 4: Grafana Dashboard

Search `https://grafana.com/grafana/dashboards/` for a community dashboard matching the service.

- If a good match is found: report the dashboard ID and name to the user, and remind them to import it in the Grafana UI on **atreides** (Dashboards → Import → enter ID).
- If no match is found: note that no community dashboard was found; the user can build a custom one.

Key existing dashboard IDs for reference: `1860` (Node Exporter Full), `17346` (Traefik), `13768` (Blocky).
````

</details>

Now those instructions only enter context when I actually invoke the command — instead of bloating every session in that repo.

One of the cooler things that you can do with the skills files is you can also have user-based skills instead of repository-based skills - user skills are located at `~/.claude/skills/<SKILL-NAME>/SKILL.md`. These are skills that you could use across machines, across repositories, wherever you have a Claude Code Terminal Session open. They're kind of like dot files but for agent skills. They even work in the webui or the desktop application (depending on what exactly you need them to do).

This solves the same issue that I had in my other post by providing a more deterministic way of making the AI behave, but it also leaves the `CLAUDE.md` file less cluttered. If your `CLAUDE.md` file gets too large you start to eat away at your context window and get diminishing results.

For more details on skills, check the [official Claude Code skills documentation](https://docs.anthropic.com/en/docs/claude-code/skills).
