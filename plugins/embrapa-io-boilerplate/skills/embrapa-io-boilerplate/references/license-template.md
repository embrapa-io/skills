# `LICENSE` — Substituição para MIT

## Por que substituir?

Em aplicações Embrapa I/O "normais" (repositórios de apps reais), o `LICENSE` costuma ser um _copyright all-rights-reserved_ da Embrapa, adequado para software institucional proprietário:

```
Copyright ⓒ <ano> Brazilian Agricultural Research Corporation (Embrapa). All rights reserved.
```

Esse modelo **não serve para boilerplates**. Um boilerplate é um template público, reutilizável por qualquer Unidade Descentralizada da Embrapa (e por qualquer desenvolvedor) para derivar software novo. Se o boilerplate carregar licença restritiva, ele **contamina** todo fork descendente — e esse não é o objetivo.

A licença **MIT** é permissiva, não-contaminante (não exige que derivados sejam MIT, não exige abertura do código derivado) e compatível com uso comercial, proprietário e open-source. É o padrão universal para templates/boilerplates.

## Código de terceiros: o aviso original fica

Antes de substituir, leia o `LICENSE` atual. Se a app nasceu de código de terceiros com licença permissiva (um
_template_ da comunidade, uma biblioteca incorporada), **o aviso de _copyright_ original não pode sair**: a própria MIT
exige que «the above copyright notice and this permission notice shall be included in all copies». Trocar o arquivo
inteiro pelo da Embrapa descumpre a licença do autor original.

| `LICENSE` atual | O que fazer |
| --- | --- |
| _All rights reserved_ da Embrapa (app institucional) | substituir pelo modelo abaixo, como de costume |
| MIT de terceiros | manter o texto MIT e **acrescentar** a linha da Embrapa abaixo da original (as duas ficam) |
| BSD, ISC ou Apache 2.0 de terceiros | não trocar a licença: manter o arquivo original e acrescentar a linha da Embrapa, se a licença permitir; confirmar com o usuário |
| GPL, AGPL, LGPL ou sem licença | parar e avisar o usuário: o código não pode virar _boilerplate_ MIT sem autorização do autor |

Exemplo (MIT de terceiros):

```
MIT License

Copyright (c) 2019 Sebastián Ramírez
Copyright (c) <ANO> Brazilian Agricultural Research Corporation (Embrapa)

Permission is hereby granted, ...
```

Diga ao usuário, no _diff_ final, que o aviso de terceiros foi mantido e por quê.

## Quando aplicar

Durante a genericação, substitua o conteúdo do `LICENSE` pela licença MIT com o **ano atual** (ano de quando a genericação está sendo feita). Não use `%GENESIS_ACTUAL_YEAR%` aqui — o placeholder é processado em `README.md` pela plataforma, mas o `LICENSE` vai como literal no fork. Use o ano corrente obtido de `date +%Y` ou do contexto da conversa.

## Template canônico

Copie **exatamente** este conteúdo (substituindo `<ANO>` pelo ano atual):

```
MIT License

Copyright (c) <ANO> Brazilian Agricultural Research Corporation (Embrapa)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Regras

- **Titular do copyright é a Embrapa** (`Brazilian Agricultural Research Corporation`), ao lado do autor original quando houver código de terceiros. Não mude o titular, não coloque nome pessoal, nem nome da Unidade Descentralizada. O boilerplate é propriedade institucional.
- **Ano** = ano corrente no momento da genericação. Não `1988`, não `%PLACEHOLDER%`, não o ano do primeiro commit do repo original.
- **Não traduza** o texto da licença para português. O texto canônico MIT precisa ficar em inglês por razões jurídicas (é a forma reconhecida internacionalmente).
- **Arquivo sem extensão** (`LICENSE`, não `LICENSE.md` nem `LICENSE.txt`) — convenção Embrapa I/O.
- **Final do arquivo**: terminar com quebra de linha final (`\n`). Evita o aviso "No newline at end of file" em diffs.

## Checagem pós-substituição

Depois de substituir, confirme com um `cat LICENSE` ou leitura que:

- [ ] Primeira linha é `MIT License` (literal)
- [ ] Avisos de _copyright_ de terceiros que existiam continuam no arquivo
- [ ] Linha de copyright da Embrapa contém ano atual (4 dígitos) e `Brazilian Agricultural Research Corporation (Embrapa)`
- [ ] Texto canônico da MIT presente (parágrafos: "Permission is hereby granted", "The above copyright notice", "THE SOFTWARE IS PROVIDED")
- [ ] Arquivo termina com quebra de linha

## O que NÃO fazer

- ❌ Não use Apache 2.0, GPL, BSD ou outra licença sem alinhar com o usuário — MIT é a padrão do boilerplate.
- ❌ Não remova o `LICENSE` por achar que "a plataforma gera depois". Ela não gera.
- ❌ Não deixe o copyright antigo da Embrapa ("All rights reserved") no arquivo — substitua **integralmente**.
- ❌ Não apague o aviso de _copyright_ de terceiros (MIT, BSD, Apache): ele fica, com a linha da Embrapa acrescentada.
- ❌ Não adicione cabeçalho de licença em arquivos de código-fonte. O `LICENSE` raiz é suficiente.
