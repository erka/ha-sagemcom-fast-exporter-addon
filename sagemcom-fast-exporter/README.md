# Home Assistant Add-on: Sagemcom Fast Exporter

A Home Assistant add-on that exposes metrics from your Sagemcom F@st series fibre hub/router to Prometheus. This add-on packages the [sagemcom_fast_exporter](https://github.com/hairyhenderson/sagemcom_fast_exporter) for easy integration with Home Assistant.

## Quick Start

The add-on requires:

- **Host**: IP address of your Sagemcom device (default: `192.168.2.1`)
- **Password**: Device password (usually the serial number)

Once running, metrics are available at: `http://<your-home-assistant-addon-hostname>:9780/scrape`

## Configuration

Key options:

- `host` - Device IP address
- `username` - Login username (default: `admin`)
- `password` - Login password (required)
- `addr` - Exporter listen address (default: `0.0.0.0:9780`)
- `authMethod` - Authentication method (SHA512 or MD5)
- `logLevel` - Logging level (error, info, debug)
- `scraper` - Scraper (standard or lite)

## Prometheus Integration

Add to your Prometheus configuration:

```yaml
scrape_configs:
  - job_name: gigahub
    metrics_path: /scrape
    scrape_timeout: 30s
    static_configs:
      - targets:
          - "<your-home-assistant-addon-hostname>:9780"
```

## Grafana Dashboard

A Grafana dashboard is available ([ID: 20374](https://grafana.com/grafana/dashboards/20374)) for visualizing metrics.

## Credits

- Original project: [hairyhenderson/sagemcom_fast_exporter](https://github.com/hairyhenderson/sagemcom_fast_exporter)

## License

[MIT License](https://github.com/erka/ha-sagemcom-fast-exporter-addon/blob/main/LICENSE)
