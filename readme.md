# How to Setup Cloudflare Tunnel for Your Home Server
## Step 1
Get Cloudflare Tunnel Token and fill in .env

## Step 2
```
docker compose up -d
```

## Step 3 Configure the public Hostnames

## Step 4 Home Router: Set port forwarding for each port


### You can get the tunnel token through the Cloudflare dashboard:

**Step 1: Access Cloudflare Zero Trust Dashboard**
- Go to https://dash.cloudflare.com
- Select your account
- Go to **Zero Trust** (left sidebar)
- Click **Networks** → **Tunnels**

**Step 2: Create or Select Tunnel**
- Click **Create a tunnel** (or select existing tunnel)
- Choose **Cloudflared** as connector type
- Give it a name (e.g., "my-tunnel")
- Click **Save tunnel**

**Step 3: Get the Token**
- After creating the tunnel, you'll see the installation instructions
- Look for the Docker command that looks like:
```bash
docker run cloudflare/cloudflared:latest tunnel --no-autoupdate run --token eyJhIjoiYWJjZGVmZ2hpams...
```
- Copy everything after `--token ` - that's your tunnel token

**Step 4: Configure Routes (Important)**
- In the **Public Hostnames** tab, add your routes:
  - **Subdomain**: your-app
  - **Domain**: yourdomain.com  
  - **Service**: http://your-service:port (e.g., http://localhost:3000)
- Click **Save**

**Alternative: Get token from existing tunnel**
- Go to **Zero Trust** → **Networks** → **Tunnels** 
- Click on your existing tunnel name
- Click **Configure**
- The token will be shown in the connector installation section

The token is the long string starting with `eyJ...` - copy the entire thing into your `.env` file.