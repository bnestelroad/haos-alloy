# Changelog

## 1.1.0-fleet.1 — bnestelroad fork

Fork of `Whizzlefred/haos-alloy` for the exitinterview.sh fleet. See ADR-HOME-015.

- Add `job = "homeassistant"` and `instance = "homeassistant"` static labels so
  logs match the fleet's `job`-based query convention (Robot Rollcall checks,
  the `unifi` syslog pipeline).
- Change `env` label `prod` → `production` to match existing fleet targets.
- Default `loki_url` to the fleet Loki (`http://192.168.1.10:3100/loki/api/v1/push`).

## 1.1.0

- Add `ca_cert_file` option for custom CA certificate support (Closes #7)
- Add `ssl:ro` volume mapping for `/ssl/` directory access

## 1.0.1

- Fix: correct journal field names in relabel rules (`syslog_identifier`, `container_name`)
- Fix: remove non-existent `PRIORITY_KEYWORD` level relabel rule (Loki `detected_level` handles this automatically)

## 1.0.0

- Initial release
- Ship systemd journal logs to Loki via Grafana Alloy v1.13.1
- Auto-detect journal path (`/var/log/journal` or `/run/log/journal`)
- Configurable Loki URL, log level, and additional Alloy config blocks
- Static labels: `host`, `env`, `source_type`, `service`, `retention`
- Journal field extraction: `unit`, `hostname`, `syslog_identifier`,
  `transport`, `container_name`, `level`
- Alloy debug UI on port 12345
- Support for `amd64` and `aarch64` architectures
