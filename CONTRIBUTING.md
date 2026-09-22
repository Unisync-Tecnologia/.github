# 🚀 Guia de Contribuição e Fluxo de Branches (Git Flow)

Obrigado por ajudar a construir e evoluir as soluções da **Unisync Tecnologia**. Para garantir a estabilidade dos nossos sistemas de saúde e evitar quebras em produção, adotamos um modelo baseado no **Git Flow**.

---

## 🌿 A Árvore de Branches da Unisync

Nosso código é dividido em três níveis principais de responsabilidade:

1. **`main` (Produção):** Contém o código sagrado e estável que está rodando nas clínicas em tempo real. **Ninguém desenvolve ou faz commit direto aqui.**
2. **`develop` (Homologação/Rascunho):** É o ponto central onde todas as novas funcionalidades se encontram. É usada para testes internos e validações.
3. **`feature/*` ou `fix/*` (Desenvolvimento):** Ramos temporários criados por você para trabalhar em uma tarefa isolada.

---

## 🔄 Ciclo de Desenvolvimento Passo a Passo

### 1. Criando sua Branch de Trabalho
Sempre puxe uma nova branch a partir da **`develop`** atualizada:
```bash
git checkout develop
git pull origin develop
git checkout -b feature/nome-da-funcionalidade
```
* Use o prefixo `feature/` para novos recursos (ex: `feature/modulo-nefrologia`).
* Use o prefixo `fix/` para correção de bugs (ex: `fix/carregamento-laudo-pdf`).

### 2. Sincronização Diária (Evite o "Merge Hell")
Se a sua funcionalidade for grande e demorar dias para ser concluída, a `develop` vai continuar mudando enquanto você trabalha. Para evitar conflitos gigantescos no final, **atualize sua branch todo início de dia**:
```bash
git checkout develop
git pull origin develop
git checkout feature/nome-da-funcionalidade
git merge develop
```
*Resolva pequenos conflitos na sua máquina diariamente, em vez de deixar tudo para o final.*

### 3. Finalizando e Enviando para Testes (`develop`)
Quando terminar a sua feature (ou uma parte importante dela que já possa ser testada):
1. Envie sua branch para o GitHub (`git push origin feature/nome-da-funcionalidade`).
2. Abra um **Pull Request** apontando da sua branch para a branch **`develop`**.
3. Preencha o template de Pull Request de forma clara e peça a revisão de um colega.

### 4. O Caminho até a Produção (`main`)
Funcionalidades grandes podem acumular e residir na branch `develop` até o término completo do escopo e validação do time de produto. 

A fusão da `develop` para a `main` (gerando uma nova versão do sistema para as clínicas) é feita de forma planejada por meio de uma branch de `release/*`, apenas pelos administradores do repositório.

---

## 💬 Padrão de Commits
Utilize mensagens claras, em português, escritas no presente:
* `feat: adiciona filtro de pacientes por CPF`
* `fix: corrige quebra de layout no painel do médico`
