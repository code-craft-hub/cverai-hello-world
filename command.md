34.70.242.109

gcloud compute instances create cverai-instance \
  --project=pelagic-gist-459620-q8 \
  --zone=us-central1-a \
  --machine-type=e2-micro \
  --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default \
  --maintenance-policy=MIGRATE \
  --provisioning-model=STANDARD \
  --tags=http-server,https-server \
  --create-disk=auto-delete=yes,boot=yes,device-name=cverai-instance,image=projects/debian-cloud/global/images/debian-12-bookworm-v20241009,mode=rw,size=30,type=pd-balanced \
  --no-shielded-secure-boot \
  --shielded-vtpm \
  --shielded-integrity-monitoring \
  --labels=environment=production,app=cverai \
  --reservation-affinity=any

  gcloud compute firewall-rules list

sudo apt update && sudo apt upgrade -y
