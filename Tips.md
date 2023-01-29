# Information
## Firewall used: nftables
- Config file: /etc/nftables.conf
- Helpful documentation: https://wiki.nftables.org/wiki-nftables/index.php/Quick_reference-nftables_in_10_minutes
- Helpful commands:
  - SAVE RULESET: nft list table filter > nftables.conf
  - RESTORE RULESET: nft -f nftables.conf
## Tmux
- Cheat Sheet: https://tmuxcheatsheet.com/
- Commands:
  - Detach from current session: Ctrl + b d
  - List all sessions: tmux ls
  - Attach to last session: tmux a
  - Attach to 'mysession': tmux a -t mysession
## Server Load Balancer: Nginx
- Config file: /etc/nginx/nginx.conf
- Available Websites: /etc/nginx/sites-available/
- Enabled Websites: /etc/nginx/sites-enabled/
- Access Log: /var/log/nginx/access.log
- Error Log: /var/log/nginx/error.log
- Create symlink: ln -s [source] [destination]
## Website Reverse Proxy: Cloudflare
- Dashboard: https://dash.cloudflare.com/b686410026ae13ac7abe3d38a70af4aa/kcmozou.com
## Domain Hosting: Namecheap
- Dashboard: https://ap.www.namecheap.com/dashboard
