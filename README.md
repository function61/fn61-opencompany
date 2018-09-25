In this repo I'd like to open up details about how I run the company, its webservices and develop apps.

TODO: more openness. Inspired by [opencompany/awesome-open-company](https://github.com/opencompany/awesome-open-company)


Infrastructure level decisions
------------------------------

| Problem (link = more details)   | Solution                                                                   |
|---------------------------------|----------------------------------------------------------------------------|
| [Cloud](docs/selecting-a-cloud-provider.md) | DigitalOcean                                                               |
| Cloud lock-in                   | Only compute to maximize portability, everything else like queues from AWS |
| Single or multi-DC availability | Multi-DC, probably multi-vendor as well for safety                         |
| OS                              | CoreOS with auto-updates disabled                                          |
| Infrastructure immutability     | Packer + Terraform                                                         |
| PKI                             | Root CA in Yubikey, cfssl                                                  |
| Secure auth to SSH              | Agent + Yubikey                                                            |
| Containerization                | Docker                                                                     |
| Orchestration                   | Docker Swarm                                                               |
| Container cross-host networking | Docker Swarm                                                               |
| Orchestration dashboard         | Portainer                                                                  |
| Backups                         | TODO                                                                       |
| DDOS protection                 | Cloudflare                                                                 |
| Logging                         | LogEntries                                                                 |
| Alerting                        | function61/lambda-alertmanager                                             |
| Website uptime monitoring       | alertmanager-canary (sub-project of lambda-alertmanager)                   |
| Metrics                         | Prometheus                                                                 |
| Metrics dashboard               | Grafana                                                                    |
| Container secrets               | ENV variable injection via orchestration                                   |
| Edge routing                    | Traefik                                                                    |


Application level decisions
---------------------------

| Problem                         | Solution                                                                   |
|---------------------------------|----------------------------------------------------------------------------|
| Programming language            | Go                                                                         |
| Build system                    | Turbo Bob                                                                  |
| Persistence                     | Eventhorizon + BoltDB                                                      |
| Session mechanism               | JWT                                                                        |
| Auth methods                    | SSO(password, TOTP, U2F)                                                   |


Miscellaneous design decisions
------------------------------

| Problem                      | Solution                      |
|------------------------------|-------------------------------|
| Payment traffic              | Stripe                        |
| Accounting                   | ledger-cli                    |
| Developer secrets management | function61/pi-security-module |
