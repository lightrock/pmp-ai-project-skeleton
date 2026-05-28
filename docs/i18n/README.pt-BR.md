Para a introdução pública, veja o [site do Doctor Bones no GitHub Pages](https://lightrock.github.io/drbones/).

# Doctor Bones

Doctor Bones é um modelo de repositório independente de fornecedor para desenvolvimento assistido por IA.

Ele ajuda você a manter a memória do projeto dentro do repositório, em vez de presa no chat. Ele dá ao seu time humano/IA uma disciplina operacional compartilhada: ordens de trabalho, playbooks, exemplos, verificações, regras de passagem de contexto e hábitos de prontidão para releases.

A ideia é que, sempre que você começar um novo projeto, comece com um Doctor Bones.

Você não precisa necessariamente baixar a sua cópia deste modelo para o seu PC local ou ambiente de agente para usá-lo. O Doctor Bones carrega sua arquitetura cognitiva no próprio repositório. Se você seguir as instruções de início abaixo, sua IA de primeiro plano deve ter inteligência de projeto suficiente para raciocinar a partir da orientação do repositório, dos exemplos, dos playbooks, das verificações e das regras de passagem de contexto.

Por padrão, nada precisa "rodar" em lugar nenhum da forma tradicional, e você não precisa necessariamente invocar um executor como o Codex. Aponte primeiro sua IA de primeiro plano para a instância adequada de repositório baseada em Doctor Bones. Use um executor apenas quando a tarefa exigir edições de arquivos, ambiente de execução, verificações, commits ou pull requests.

## Mais sobre a ideia

Antes de a IA programar, ensine o repositório a falar. Antes de a IA afirmar que terminou, defina o que terminado significa. Antes de a IA recomendar, separe evidência de conclusão. Antes de a IA aplicar um patch, defina autoridade, verificação e regras de fronteira.

Podemos definir padrões nativos do repositório que Cursor, Codex, Claude Code, Copilot... e bots do GitHub devem obedecer?

Podemos facilitar a adaptação disso às suas necessidades específicas?

## Em andamento / TODO / A TERMINAR

Veja [TODO.md](../../TODO.md) para a lista aproximada do que ainda precisa virar arquivos de repositório, esquemas, rubricas, exemplos, verificações e alvos de integração.

## Idiomas

- [English](../../README.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- [Deutsch](README.de.md)
- Português do Brasil: este arquivo
- [हिन्दी](README.hi.md)

## O que é isto

É uma camada de disciplina nativa do repositório para usar assistentes de IA e agentes de programação sem perder intenção, restrições, verificações ou histórico do projeto.

O modelo básico é:

```text
intenção humana
→ a IA de primeiro plano esclarece a tarefa
→ o repositório captura orientação durável
→ a IA executora realiza trabalho delimitado
→ as verificações validam o que pode ser verificado
→ a conclusão se conecta de volta à intenção de origem
```

Pense na IA de primeiro plano como a assistente de planejamento e arquitetura. Pense na IA executora como o trabalhador com acesso a arquivos, ambiente de execução, testes e ferramentas de commit/PR.

O repositório é a camada de memória e disciplina entre os dois.

## Primeiros passos

1. Se você copiou este modelo, reescreva este README em torno do seu projeto real em breve.
2. Leia [`examples/README.md`](../../examples/README.md) para ver os exemplos de fluxo de trabalho day-in-the-life.
3. Leia [`readme_pmp.md`](../../readme_pmp.md) pelo menos uma vez e mantenha-o por perto.
4. Leia [`AGENTS.md`](../../AGENTS.md) antes de pedir a um assistente de IA para alterar o repositório.
5. Use uma ordem de trabalho para trabalhos substanciais, com vários arquivos, sensíveis à arquitetura ou sensíveis ao processo.
6. Execute as verificações disponíveis antes de tratar o trabalho como concluído.

## Limite de processo

Não crie as ordens de trabalho do seu projeto no repositório-fonte público do Doctor Bones, a menos que você esteja contribuindo intencionalmente com o próprio Doctor Bones.

Para o seu próprio projeto, primeiro crie ou use seu próprio repositório a partir deste modelo. Depois, aponte sua IA de primeiro plano para a URL desse repositório de projeto e crie as ordens de trabalho lá.

Use `lightrock/drbones` como modelo-fonte, implementação de referência e projeto upstream. Use seu repositório copiado baseado em Doctor Bones como o local onde vivem a memória do seu projeto, as ordens de trabalho, as lições aprendidas e as mudanças específicas do projeto.

## Prompt de início para a IA de primeiro plano

Este prompt é para um repositório criado a partir do modelo Doctor Bones. Depois de copiar este modelo, substitua `<your project repository URL>` pela URL do seu próprio repositório de projeto.

Ao iniciar um novo chat ou aba para o repositório do seu projeto, cole isto na IA de primeiro plano:

```text
You are the foreground AI for <your project repository URL>.

Current repo state beats chat memory. Inspect the current project repository before giving
architecture advice, writing workorders, or suggesting repo changes.

Read README.md, examples/README.md, readme_pmp.md, AGENTS.md, and the relevant folder
guidance from the project repository first. Then identify current state, target, constraints,
foreground/executor decision, and the smallest useful next move.
```

## Atalho de ordem de trabalho

Para trabalho substancial no seu repositório de projeto copiado, converse com a IA de primeiro plano até que a tarefa esteja clara, depois diga:

```text
Create a workorder and also show it to me here.
```

Você pode copiar um link para o arquivo da ordem de trabalho e dizer à sua IA executora, trabalhando em um ambiente para o repositório do seu projeto, para executá-la.

Você também pode copiar/colar o corpo da ordem de trabalho se pediu à IA de primeiro plano para mostrá-lo primeiro. Mantenha esse bloco de copiar/colar limpo: sem citações, notas do assistente, explicações, links extras ou comentários dentro do corpo da ordem de trabalho.

## Verificações

Execute estes comandos a partir da raiz do repositório quando disponíveis:

```text
python tools/pmp_check.py --area all
python -m pytest
```

Se uma verificação falhar, cole a saída exata do comando na IA de primeiro plano e peça a menor correção segura.
