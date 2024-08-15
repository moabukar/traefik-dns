# Traefik DNS (Cloudflare)

## Step by step config:

- Create a VM and install docker. Clone this repo
- Create Cloudflare token with Zone/Zone Read and Zone/DNS edit. 
    - put these secrets in the folder secrets `secrets` and create files `cloudflare-email.secret` and `cloudflare-token.secret`. Place your cloudflare email and cloudflare scoped api token here.
- Run docker compose file and update your domain in line 31,32
    `- --entrypoints.websecure.http.tls.domains[0].main=dev.moabukar.co.uk`
    `- --entrypoints.websecure.http.tls.domains[0].sans=*.dev.moabukar.co.uk`
    - Also update the routes for your apps.

- In cloudflare, add an `A` record and point it to the public IP of your VM
- In security groups, open ports 80 & 443 to allow traffic for Traefik to work properly.
- Run the docker compose with `docker compose up -d`
- Now access your apps `app.yourdomain.co.uk`
- You should see the apps working with SSL via Let's encrypt
