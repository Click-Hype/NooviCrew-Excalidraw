# NooviCrew — fork do Excalidraw

Fork de [`excalidraw/excalidraw`](https://github.com/excalidraw/excalidraw) usado como
**editor de diagramas self-hosted** da NooviCrew.

- **No ar:** https://map.noovicrew.com (editor puro, sem backend de colaboração/sync).
- **Origin:** `Click-Hype/NooviCrew-Excalidraw` · **Upstream:** `excalidraw/excalidraw`
  (puxar updates: `git fetch upstream && git merge upstream/master`).
- **Como roda:** imagem Docker buildada do `Dockerfile` deste repo
  (build `yarn` → estáticos servidos por `nginx:80`), publicada como stack Swarm.

## Deploy (produção)

Imagem: `noovicrew-excalidraw:local` · Stack: `excalidraw` · Compose e labels Traefik em
`/home/debian/docker/stacks/excalidraw/docker-compose.yml` (fora do repo).

```bash
# no host do servidor
docker build -t noovicrew-excalidraw:local .
docker stack deploy -c /home/debian/docker/stacks/excalidraw/docker-compose.yml excalidraw
```

Roteamento por `map.noovicrew.com` via Traefik (`websecure` + certresolver `le`, TLS
Let's Encrypt automático). Sem estado no servidor — os desenhos ficam no storage do browser
do usuário / arquivos `.excalidraw` exportados.

## MCP

O toolkit de agentes (fork de `yctimlin/mcp_excalidraw`) fica em `MCP/`
(repo `Click-Hype/NooviCrew-Excalidraw-MCP`, nested; excluído do tracking deste fork via
`.git/info/exclude`). Ver `MCP/NOOVICREW.md`.
