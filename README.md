In this repo I'd like to open up details about how I run the company, its webservices and develop apps.

TODO: more openness. Inspired by [opencompany/awesome-open-company](https://github.com/opencompany/awesome-open-company)


Infrastructure level decisions
------------------------------

| Problem (link = more details)   | Solution                                                                   |
|---------------------------------|----------------------------------------------------------------------------|
| [Cloud](docs/selecting-a-cloud-provider.md) | [DigitalOcean](https://www.digitalocean.com/)                  |
| Cloud lock-in                   | Only compute to maximize portability, everything else like queues from AWS |
| Single or multi-DC availability | Multi-DC, probably multi-vendor as well for safety                         |
| OS                              | [CoreOS](https://coreos.com/os/docs/latest/) with auto-updates disabled    |
| Infrastructure immutability     | [Packer](https://www.packer.io/) + [Terraform](https://www.terraform.io/)  |
| PKI                             | Root CA in Yubikey, [cfssl](https://github.com/cloudflare/cfssl)           |
| Secure auth to SSH              | Agent + [Yubikey](https://www.yubico.com/products/yubikey-hardware/)       |
| Containerization                | [Docker](https://www.docker.com/)                                          |
| Orchestration                   | [Docker Swarm](https://docs.docker.com/engine/swarm/)                      |
| Container cross-host networking | [Docker Swarm](https://docs.docker.com/engine/swarm/)                      |
| Orchestration dashboard         | [Portainer](https://portainer.io/)                                         |
| Backups                         | Cloud provider's VM snapshots for now (TODO: something more efficient)     |
| Domain registrar                | [AWS Route53](https://aws.amazon.com/route53/)                             |
| DNS                             | [Cloudflare](https://www.cloudflare.com/)                                  |
| DDOS protection                 | [Cloudflare](https://www.cloudflare.com/)                                  |
| Logging                         | [LogEntries](https://logentries.com/)                                      |
| Alerting                        | [function61/lambda-alertmanager](https://github.com/function61/lambda-alertmanager) |
| Website uptime monitoring       | alertmanager-canary (sub-project of lambda-alertmanager)                   |
| Metrics                         | [Prometheus](https://prometheus.io/)                                       |
| Metrics dashboard               | [Grafana](https://grafana.com/)                                            |
| Container secrets               | ENV variable injection via orchestration                                   |
| Edge routing                    | [Traefik](https://traefik.io/)                                             |


Application level decisions
---------------------------

While some applications require different solutions for different problems, this is the basic stack we
start with and customize from there where needed.

| Problem                         | Solution                                                                   |
|---------------------------------|----------------------------------------------------------------------------|
| Programming language            | [Go](https://golang.org/)                                                  |
| Build system                    | [Turbo Bob](https://github.com/function61/turbobob)                        |
| Log shipping                    | That's an infrastructure concern                                           |
| Persistence                     | [Eventhorizon](https://github.com/function61/eventhorizon) + [BoltDB](https://github.com/etcd-io/bbolt) |
| Session mechanism               | [JWT](https://jwt.io/)                                                     |
| Auth methods                    | SSO(password, [TOTP](https://en.wikipedia.org/wiki/Time-based_One-time_Password_algorithm), [U2F](https://www.yubico.com/solutions/fido-u2f/))                                                   |


Miscellaneous design decisions
------------------------------

| Problem                      | Solution                      |
|------------------------------|-------------------------------|
| Payment traffic              | [Stripe](https://stripe.com/) |
| Accounting                   | [ledger-cli](https://www.ledger-cli.org/) |
| Developer secrets management | [function61/pi-security-module](https://github.com/function61/pi-security-module) |
