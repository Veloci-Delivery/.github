## O que este PR faz?
<!-- Descreva brevemente as mudanças e qual problema elas resolvem -->

## Tipo de mudança
- [ ] 🐛 Correção de bug
- [ ] ✨ Nova funcionalidade
- [ ] ♻️ Refatoração / Código
- [ ] 📝 Documentação
- [ ] 🔧 Infraestrutura / CI-CD

## Como testar?
<!-- Como o revisor pode testar essas alterações? -->
1. 
2. 

## Checklist
- [ ] Revisei meu próprio diff
- [ ] Nenhuma mudança de schema sem arquivo de migração versionado (sem `db push`, `--accept-data-loss`, `migrate --fake`)
- [ ] Nenhum segredo em código, compose, log ou neste PR

## Se mexe em compose, Dockerfile, workflow ou é uma aplicação nova
<!-- Padrão de Desenvolvimento Veloci, vault: 00_Sistema/Padrao_Desenvolvimento_Veloci.md -->
- [ ] Nome do produto único em repositório, pasta `/opt/<produto>`, `name:` do compose, container, banco (§1)
- [ ] `compose.yaml` + `compose.prod.yaml`; sem `compose.override`, sem `container_name`; serviço nomeado pelo papel (`web`, `worker`, `beat`) (§3)
- [ ] Todo serviço com `mem_limit`, `cpus`, `restart: unless-stopped`, `healthcheck` (web e worker) e rotação de log (§3)
- [ ] Soma dos limites do nó continua ≤ 80% da RAM (9,3 GB) (§3)
- [ ] Porta só em `127.0.0.1`, registrada na tabela do §4
- [ ] `.env` montado somente leitura e lido no processo, nunca `env_file`/`environment` com segredo (§7)
- [ ] Deploy Node 2 → Node 1 com portão de saúde; imagem por tag do commit (§5)
- [ ] Aplicação nova: banco e papel próprios na VM de estado, incluídos no backup; nota-hub no vault; reinício da máquina testado (§10)
