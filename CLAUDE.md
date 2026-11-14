# Henrique Devens Projetos
Sistema de gestão patrimonial do cliente Henrique Devens (atleta). Arquivo único: index.html (HTML + JS puro, sem framework e sem build). Escopo: consolidar patrimônio e viabilidade, não gerir a operação dos negócios.

## Arquitetura
- Sidebar da holding: Painel consolidado, Imobiliário, Food Parks, Esporte & Impacto, Agro & Corporate, Metas, Configurações.
- Rotas: showHolding(), showNegocio(n), showImoveisPage(p), showPage(p) (só renderiza, nunca mexe na sidebar), setNavActive(id), injectImoveisTabBar(p).
- Persistência: GitHub Gist (patrimonio.json). Ordem obrigatória: loadGist antes de saveGist.
- Estado: imoveis, lancamentos, caixa, verticais, meta, historicoPL, metas.

## Regras
- Sem crases aninhadas: use concatenação de strings.
- Use data-* em vez de aspas aninhadas no onclick.
- Depois de editar, rode: extrair o <script> e fazer node --check.
- Não alterar a lógica do módulo Imobiliário sem pedido explícito.

## Lacunas conhecidas (ordem de prioridade)
1. Segurança: token do Gist criptografado e exposto no front-end, senha fraca, token salvo no localStorage, risco de XSS em innerHTML.
2. saveGist deve ser bloqueado se loadGist falhou (risco de sobrescrever o Gist).
3. Simulador de Metas (mSimular) é tautológico: sempre "viável". Projetar com retorno-base editável + aportes.
4. state.meta e state.metas duplicados: o Painel deve ler de metas.
5. Rendimento de 6% fixo no código: tornar editável.
6. Sem exportação completa (caixa, verticais, meta, historicoPL, metas) e sem @media (não é responsivo).
7. Pendente: Esporte & Impacto (Arena Garden, CT Aracruz), Food Parks e Agro.