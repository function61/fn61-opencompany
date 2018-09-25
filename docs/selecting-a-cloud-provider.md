Selecting a cloud provider
==========================

The biggest players are:

- AWS
- Google Cloud
- Microsoft Azure

Some smaller players:

- DigitalOcean
- Vultr (basically a DigitalOcean copy)
- Packet (a bare-metal cloud)
- Scaleway

Thoughts:

- A good way to gauge the serious choices are to look at [Terraform providers](https://www.terraform.io/docs/providers/),
  (also important if you're aiming for infrastructure as code and/or immutable infrastructure).
- AWS & Google Cloud's compute is not expensive, but bandwith costs are ridiculous compared to other players' options:
	* AWS $20 for 1 000 GB ($0.02/GB), Google Cloud ($0.12/GB)
	* DigitalOcean cheapest plan includes 1 000 GB for free ($0.01/GB after that), Vultr includes 500 GB for free
	* Scaleway has no transfer limit (but speed varies depending on instance type)
- Packet's cheapest plan is $50/month, but you get 8 GB of RAM
- Vultr was cheaper than DigitalOcean, but DigitalOcean recently lowered their prices so they're basically the same.
  Choosing between DigitalOcean vs. Vultr I'd go for DigitalOcean simply because it has longer track record and is more known,
  although I've had VMs running for a long time on Vultr with no problems.
- Scaleway is clearly the best regarding the price, but I wouldn't host anything mission critical there as there are
  very many red flags about people's experiences with them when Googling about them.
- As usual for Microsoft, [Azure is technically the weakest choice](https://joonas.fi/2017/01/23/microsoft-azures-networking-is-fundamentally-broken/)
  insofar that they have a forced NAT for no reason that makes some network software not work without special keepalive patches.
