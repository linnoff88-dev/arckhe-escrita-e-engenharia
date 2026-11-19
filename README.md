# Escrita e Engenharia â€” prompt com prova

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![Prompt com prova](guia/assets/banner.jpg)](https://inematds.github.io/escrita-e-engenharia/guia/)

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

Este kit ensina a escrever pedidos para a IA (o â€œpromptâ€) de um jeito que obriga a IA a **provar** o que fez, em vez de sÃ³ dizer â€œprontoâ€. SÃ£o 8 tÃ©cnicas de escrita que qualquer pessoa usa no ChatGPT, no Claude ou no Gemini, e 9 soluÃ§Ãµes de engenharia para quem monta agentes e aplicativos com IA. Vem com um modelo de pedido para copiar, exercÃ­cios, um checador que dÃ¡ nota de 0 a 8 ao seu pedido e o cÃ³digo das soluÃ§Ãµes em Python. Para usar as tÃ©cnicas basta ler; para o checador e o cÃ³digo, sÃ³ Python 3.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/escrita-e-engenharia/guia/**

## As 8 tÃ©cnicas de escrita

| # | TÃ©cnica | SeÃ§Ã£o no pedido |
|---|---|---|
| 1 | Feche com a prova (rodar e devolver nÃºmeros) | `PROVA:` |
| 2 | â€œProntoâ€ sÃ³ com checagem | `PRONTO:` |
| 3 | Avise onde costuma errar | `ONDE COSTUMA ERRAR:` |
| 4 | Um dono para cada coisa | `UM DONO:` |
| 5 | NÃºmero sensÃ­vel com nome | `NOME = valor` |
| 6 | Recibo antes de â€œfeitoâ€ | `RECIBO:` |
| 7 | Texto de fora Ã© dado, nÃ£o ordem | `TEXTO DE FORA:` |
| 8 | LiÃ§Ã£o vira regra | `LIÃ‡Ã•ES:` |

## As 9 soluÃ§Ãµes de engenharia

1. Resposta na hora, trabalho depois (`kit/rotas.py`)
2. Sinal de vida durante a espera (`kit/rotas.py`)
3. Resultado em blocos que chegam aos pedaÃ§os, conserto de no mÃ¡ximo 2 vezes (`kit/blocos.py`)
4. Mudar sÃ³ o que mudou (`kit/blocos.py`)
5. Barreira logo depois de gerar (`kit/guarda.py`)
6. Checagem de ponta a ponta que cresce com cada erro (`kit/preflight.py`)
7. A fonte manda, a cÃ³pia sai dela
8. NÃ£o passar por cima da mÃ£o da pessoa
9. Ensaio sem rastro + recibo de custo (`kit/preflight.py`, `kit/recibo.py`)

## Uso rÃ¡pido

```bash
git clone https://github.com/inematds/escrita-e-engenharia.git
cd escrita-e-engenharia
python3 -m unittest -q                              # 47 testes, OK
python3 kit/checar_prompt.py exemplos/antes.md      # nota: 0/8
python3 kit/checar_prompt.py exemplos/depois.md     # nota: 8/8
python3 kit/checar_prompt.py meu-prompt.md --minimo 8
python3 kit/preflight.py --demo                     # 4 ok, 0 falha, 0 aviso
python3 kit/preflight.py --demo --quebrar           # 1 ok, 3 falha (sai 1)
```

Modelo para copiar: [`modelos/prompt-modelo.md`](modelos/prompt-modelo.md) (tambÃ©m em [`modelos/en/`](modelos/en/prompt-modelo.md) e [`modelos/es/`](modelos/es/prompt-modelo.md)).
Skill para o Claude Code: `cp -r skill/revisar-prompt ~/.claude/skills/`.

## O processo, do inÃ­cio ao fim

| # | Passo | Comando | Quem |
|---|---|---|---|
| 1 | Escrever o pedido a partir do modelo | copiar `modelos/prompt-modelo.md` | ðŸ§  vocÃª |
| 2 | Conferir a nota do pedido | `python3 kit/checar_prompt.py meu-prompt.md --minimo 8` | âš™ï¸ script |
| 3 | Mandar o pedido para a IA | colar no chat ou no agente | ðŸ§  vocÃª |
| 4 | Exigir a prova (nÃºmeros) e o recibo na resposta | jÃ¡ estÃ¡ no pedido (`PROVA:`, `RECIBO:`) | ðŸ¤– IA |
| 5 | Conferir o sistema no ar | `python3 kit/preflight.py --alvo URL --pasta DIR --segredo .env` | âš™ï¸ script |
| 6 | Erro real â†’ linha nova em `LIÃ‡Ã•ES:` e checagem nova em `CHECAGENS_EXTRA` | editar o pedido e o `preflight.py` | ðŸ§  vocÃª |

## LicenÃ§a

MIT. Kit grÃ¡tis do [INEMA.CLUB](https://inema.club).

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>