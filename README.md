[LEIA-ME-financeiro-standalone.md](https://github.com/user-attachments/files/33670289/LEIA-ME-financeiro-standalone.md)
# Standalone do Financeiro · PBL (16/10/2026)

Arquivo: `pbl-financeiro-standalone-16-10-2026.html`. Abra no navegador: não precisa de internet nem de login.

## O que é

O menu mostra só o módulo Financeiro. As outras páginas do sistema voltam para o Financeiro.

- **Lançamentos:** Financeiro · Fluxo de Caixa · Operacional / Prod. · Campanhas · Comissões por Adv. · Comissões por Gestora · Comissões — Geração de Negócios · Resumo Consolidado · CNAB
- **Relatórios:** Relatório de Liquidados · Previsão de Entradas · Processos Liquidados · Proc. Comprados · Rel. Geral CertJud · Proc. Pendentes
- **Processos:** está no menu porque as aquisições e a venda ao FIDC ficam no painel do processo.

Os dados são **de exemplo** e ficam só na memória: lançamentos nos caixas PBL, FIDC e CERTJUD, advogados, gestoras e processos. Ao recarregar a página, tudo volta ao início. Nada é gravado no sistema de verdade.

## Onde mexer

Por dentro, o arquivo é o sistema inteiro. Para a sua alteração voltar ao sistema sem conflito, mexa **só nas funções do módulo**. Procure pelo nome da função: os números de linha mudam de uma versão para outra.

| Página | Função principal | Linha aprox. |
|---|---|---|
| Financeiro (caixas, lançamentos) | `pageFinanceiro`, `addFin`, `deleteFin`, `filterFin`, `caixaSaldos`, `upsertLancamento` | ~8444 (e ~1130) |
| Aquisições e venda ao FIDC | `procAquisicoes` … `ppVendaFidcBox` | ~8200–8440 |
| Fluxo de Caixa | `pageFluxoCaixa`, `detalharMes` | ~8551 |
| Operacional / Prod. | `pageOperacional` | ~8610 |
| Campanhas | `pageCampanhas` | ~8827 |
| Comissões por Adv. | `pageAdvogados`, `calc`, `showDetail` | ~9151 / 8906 / 9349 |
| Resumo Consolidado | `pageResumo` | ~9721 |
| Previsão de Entradas | `pagePrevisaoEntradas` | ~10046 |
| CNAB | `pageCnab` | ~11022 |
| Comissões por Gestora | `pageComissoesGestoras`, `GESTORAS_DEF` | ~11494 |
| Relatório de Liquidados | `pageRelLiqDiario` | ~12454 |
| Processos Liquidados / Comprados / Rel. Geral / Pendentes | `pageRelLiq2`, `pageRelComp`, `pageRelGeral`, `pageRelPend` | ~12573–12727 |
| Comissões — Geração de Negócios | `pageGeracaoNegocios` | ~12930 |

## Regras que não mudam pelo arquivo

Quem vê e altera essas telas no sistema de verdade é decidido também por regras do servidor:

- **Só o admin:** Financeiro, Fluxo de Caixa, Resumo Consolidado, CNAB, Previsão de Entradas, Processos Liquidados, Proc. Comprados, Rel. Geral CertJud, Proc. Pendentes e a venda ao FIDC.
- **Admin e gestora:** Operacional, Campanhas, Comissões por Adv., Comissões por Gestora e Relatório de Liquidados.

Se a alteração precisar liberar algo para outro perfil, não basta mexer no arquivo: avise, porque a regra do servidor também precisa mudar.

## Não alterar

- O bloco `/* ===== STANDALONE SHIM` no início dos scripts. Ele só simula o banco e é trocado na hora de juntar.
- Funções fora do módulo. Se precisar mexer em alguma, anote qual e por quê.

## Para devolver

Devolva o **arquivo inteiro** (de preferência com o mesmo nome e um sufixo, por exemplo `(1)`) e uma lista curta do que mudou. A junção com o sistema é feita comparando com esta versão.
