# SGS
Scripts da SGS
# 🚀 SMAX Triage Automation

Script de automação e aprimoramento de interface para o sistema SMAX (Tribunal de Justiça de São Paulo).

## 1. Instalação

### Passo 1: Instalar o Tampermonkey
1. Abra a loja de extensões do seu navegador (Chrome, Edge ou Firefox).
2. Procure por **Tampermonkey**.
3. Instale a extensão.
4. Confirme que o ícone do Tampermonkey apareceu na barra de ferramentas.

### Passo 2: Ativar Modo Desenvolvedor
1. Vá em **Gerenciar Extensões**.
2. Ative a opção **Modo do desenvolvedor** (geralmente no canto superior direito).

### Passo 3: Configurar o Tampermonkey
1. Clique no ícone do Tampermonkey e vá em **Painel de Controle** -> **Configurações**.
2. Garanta que as seguintes opções estejam marcadas (Geral / Segurança):
   - ✅ Permitir scripts de usuário
   - ✅ Permitir acesso a abas
   - ✅ Permitir requisições remotas

### Passo 4: Instalar o Script
Acesse o arquivo do script no repositório (https://github.com/DanielMacCruz/SGS221-Triagem/raw/refs/heads/master/SMAX/TRIAGEM%20-%20SMAX%20SGS221-0.1.user.js) e clique em **Raw** ou **Instalar**.
- **Automático:** O Tampermonkey deve abrir uma aba pedindo confirmação. Clique em **Instalar**.
- **Manual:** Se não abrir, copie todo o código do .JS, vá no Tampermonkey -> **+ (Criar novo script)**, cole o código e salve (`Ctrl+S`).

---

## 2. Configuração Inicial

Ao abrir o SMAX na tela de chamados (`Requests`), uma **engrenagem** aparecerá no canto inferior direito. Clique nela para configurar.

### 2.1 Equipes e Roteamento
O sistema permite gerenciar múltiplas equipes (ex: **JEC**) e definir regras automáticas de sugestão baseadas no **Local de Divulgação** e/ou **Grupo de Suporte (GSE)** do chamado.

1. **Criar Equipe:** Clique em `+ Nova Equipe`.
2. **Definir Regras de Roteamento:**
   - **GSE:** Adicione grupos que pertencem a esta equipe.
   - **Local de Divulgação:** Adicione termos (ex: "JUIZADO ESPECIAL CIVEL") para que chamados com esse local sejam sugeridos automaticamente para esta equipe.
3. **Adicionar Membros:**
   - Use a busca ("🔍 Buscar pessoa...") para encontrar e adicionar atendentes.
   - **Dígitos Finais:** Configure os finais de cada um (ex: `00-05, 10-15`).
   - **Ausente:** Marque a caixa "Ausente" para quem não deve receber chamados (o sistema redistribui automaticamente).

> **Nota:** A equipe **GERAL** é padrão e captura tudo que não cair nas regras específicas. Nela, não é possível editar filtros de GSE ou Local.

### 2.2 Configurações Pessoais
- **Triador (Você):** No campo "Triador (quem está operando)", busque e selecione seu próprio nome. Isso é importante para vincular ações de triagem a você.

---

## 3. HUD de Triagem (Interface Principal)

Clique em **INICIAR TRIAGEM** (botão flutuante azul, canto inferior) para abrir o HUD.

### Cabeçalho e Filtros
O topo do HUD foi organizado para facilitar o fluxo de leitura da esquerda para a direita:
1. **Local de Divulgação:** Mostra a origem do chamado (ex: "JUIZADO ESPECIAL CÍVEL DA COMARCA DE JUNDIAÍ").
2. **Meus Finais:** Define quais chamados você vai processar. Ex: `00-50`.
3. **GSE:** Dropdown para visualizar ou alterar o Grupo de Suporte.
4. **Controles:** Botões de navegação (`<` `>`), atualizar fila (`↻`) e sair.

### Processo de Triagem
1. **Navegação:** Use as setas ou atalhos para passar os chamados.
2. **Urgência & Atribuição:**
   - Ao clicar em uma urgência (Baixa, Média, Alta, Crítica), o sistema **automaticamente**:
     1. Define a urgência.
     2. **Calcula o Dono:** Baseado nos dígitos finais do chamado e na lista de membros da equipe sugerida.
     3. Prepara o chamado para envio ("Pending" -> "Staged").
   - O campo de **Responsável** (dropdown) ficará com uma **borda verde brilhante** indicando que a atribuição está pronta.
3. **Respostas Rápidas:**
   - Se digitar uma solução no editor de texto, ela será enviada ao clicar em ENVIAR.
   - Chamados respondidos **não são redistribuídos** (continuam com você/triador se não houver dono específico).
4. **Envio:** Clique em **ENVIAR** para gravar todas as alterações de uma vez.

### Funcionalidades Extras
- **Anexos:** Exibidos no canto inferior direito. Clique para visualizar.
- **Discussões:** Histórico de interações à esquerda.
- **Log de Atividades:** Nas configurações (engrenagem), você pode exportar um CSV com todo o histórico de sua triagem.

---

## 4. Dicas de Uso
- **Ausências:** Mantenha o cadastro da equipe atualizado. Se alguém sai de férias, marque "Ausente" na configuração para que os chamados dessa pessoa sejam redistribuídos para os presentes.
- **GSE/Local:** Se um chamado cair na equipe errada, verifique se o "Local de Divulgação" ou "GSE" está configurado corretamente nas regras da equipe nas Configurações.
