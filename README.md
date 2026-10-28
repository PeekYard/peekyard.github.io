# Peekyard

Vitrine estática de projetos da organização [PeekYard](https://github.com/PeekYard). A homepage ficará em https://peekyard.com após configurar GitHub Pages e DNS.

## Arquivos
- `index.html`: página principal.
- `assets/style.css`: estilo responsivo.
- `assets/app.js`: catálogo e filtros sem backend.
- `projects.json`: lista de projetos (começa vazia).
- `.nojekyll`: conteúdo estático sem Jekyll.

## Adicionar projeto
1. Crie um repositório público `PeekYard/nome-do-projeto` com `index.html` e recursos com caminhos relativos.
2. Em Settings → Pages habilite publicação de `main`, diretório `/(root)`. Não configure um domínio personalizado nesse repositório.
3. Confira `https://peekyard.com/nome-do-projeto/` depois da publicação.
4. Inclua no catálogo `projects.json` via PR:
```json
{"slug":"nome-do-projeto","name":"Nome do projeto","description":"Descrição breve","category":"Tecnologia","color":"#e5dffd"}
```
O campo `color` é opcional. O slug usa letras minúsculas, números e hifens.

## Publicação da vitrine
- Repositório principal: `PeekYard/peekyard.github.io`.
- Configure Settings → Pages → Deploy from a branch → `main` → `/(root)`.
- Configure Settings → Pages → Custom domain como `peekyard.com` e, depois, Enforce HTTPS.
- Aponte registros DNS A da raiz aos endereços oficiais do GitHub Pages e CNAME `www` para `peekyard.github.io`. Consulte https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- Recomenda-se verificar o domínio em configurações da organização.
- Configure regras de proteção da branch e revisões obrigatórias em Settings → Rules → Rulesets. O PR por si só não ativa Pages nem aplica essas regras.

## Atenção
Sites em `peekyard.com/slug` compartilham a mesma origem do navegador; trate scripts de terceiros como potencialmente capazes de acessar dados de outros projetos. Revise conteúdo e dependências antes do merge. Evite dados sensíveis e autenticação nesse domínio; hospede projetos não confiáveis em origens isoladas. Avalie também os termos de uso do GitHub Pages antes de oferecer serviços comerciais.
