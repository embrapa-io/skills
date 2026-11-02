# Skills do Embrapa I/O

_Skills_ oficiais da plataforma [**Embrapa I/O**](https://embrapa.io) para o [**Claude Code**](https://claude.com/claude-code),
distribuídas como um _marketplace_ de _plugins_. Cada _plugin_ traz uma _skill_ com as instruções, os modelos e as
referências de um processo da plataforma.

## Instalação

No Claude Code, adicione este repositório como _marketplace_ e instale o _plugin_ desejado:

```
/plugin marketplace add embrapa-io/skills
/plugin install embrapa-io-boilerplate@embrapa-io-skills
```

Para receber as atualizações depois: `/plugin marketplace update embrapa-io-skills`.

## Skills disponíveis

| _Plugin_ | O que faz | Documentação |
| --- | --- | --- |
| `embrapa-io-boilerplate` | Transforma uma aplicação já aderente à plataforma (validada pela agente [Alice](https://github.com/embrapa-io/alice)) em um _boilerplate_ do catálogo: troca os valores do projeto pelos _placeholders_ `%GENESIS_*%` em `.env.io.example`, `.env.example` e `README.md`, ajusta a licença para MIT (mantendo avisos de terceiros), prepara o `.gitlab-io.yml` e orienta a análise do SonarQube antes da publicação. | [Boilerplates](https://embrapa.io/docs/boilerplate) |

A conformidade de uma aplicação com a plataforma (Docker Compose, variáveis de ambiente, serviços de _backup_,
_restore_ e _sanitize_, integrações com Sentry, Matomo e SonarQube) é tratada pela **Alice**, em
[github.com/embrapa-io/alice](https://github.com/embrapa-io/alice).

## Estrutura

```
.claude-plugin/marketplace.json        # catálogo dos plugins
plugins/<plugin>/.claude-plugin/plugin.json
plugins/<plugin>/skills/<skill>/SKILL.md (+ references/, assets/)
```

Uma _skill_ nova entra como um _plugin_ novo em `plugins/` e uma entrada em `marketplace.json`. Nomes de _plugins_,
_skills_ e arquivos em inglês; instruções e documentação em português.

## Licença

[MIT](LICENSE).
