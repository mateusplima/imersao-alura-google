# Projeto Alura-Google Gemini: Agente de Busca de Vagas Inteligente

Este projeto demonstra a criação de um sistema inteligente de busca de vagas de emprego utilizando a API do Google Gemini e o framework de agentes do Google ADK. O sistema é composto por múltiplos agentes que colaboram para coletar informações do usuário, buscar vagas relevantes no Google e apresentar as oportunidades mais compatíveis de forma organizada.

## Visão Geral

O projeto implementa um fluxo de trabalho com os seguintes agentes:

1.  **Agente de Extração de Perfil (Simplificado):** Coleta informações básicas do usuário sobre sua área de atuação, local de trabalho desejado, pretensão salarial (opcional), tempo de experiência, preferência por trabalho remoto e disposição para trabalhar em cidades próximas.

2.  **Agente de Busca de Vagas:** Utiliza a ferramenta de busca do Google para encontrar vagas de emprego relevantes com base no perfil do candidato fornecido pelo Agente de Extração de Perfil. Ele gera múltiplas consultas de busca combinando palavras-chave importantes e considera preferências como trabalho remoto e disposição para mudar de cidade.

3.  **Agente de Filtragem e Compatibilidade de Vagas:** Analisa os resultados da busca de vagas e o perfil do candidato para avaliar a compatibilidade de cada vaga. Atribui uma pontuação de compatibilidade (0-100) e filtra as vagas, mantendo apenas aquelas com uma pontuação superior a 50.

4.  **Agente de Apresentação de Vagas:** Formata e apresenta as vagas mais compatíveis de forma clara e amigável. As vagas são exibidas em uma lista numerada, ordenadas pela pontuação de compatibilidade, com informações relevantes como título, empresa, localização, pontuação e um breve motivo da compatibilidade, além do link da vaga.

## Como Funciona

1.  O script inicia chamando a função `iniciar_busca_vagas_orquestrada()`.
2.  O `agente_extrator_perfil` solicita ao usuário informações sobre seu perfil profissional e preferências de trabalho.
3.  As informações coletadas são processadas pelo `agente_extrator_perfil` para criar um resumo do perfil do candidato.
4.  O `agente_buscador_vagas` recebe o perfil processado e utiliza a ferramenta de busca do Google para encontrar vagas relevantes. As buscas consideram os critérios fornecidos pelo usuário, como área de atuação, local de trabalho e preferências de trabalho remoto.
5.  Os resultados da busca são então enviados para o `agente_compatibilidade`, que compara cada vaga com o perfil do candidato, atribui uma pontuação de compatibilidade e filtra as vagas menos relevantes.
6.  Finalmente, o `agente_apresentacao` formata as vagas mais compatíveis e as exibe para o usuário com detalhes importantes e a respectiva pontuação de compatibilidade.

## Pré-requisitos

* **Conta Google Cloud:** É necessário ter uma conta Google Cloud com a API Gemini ativada.
* **Chave de API do Google Gemini:** Uma chave de API válida do Google Gemini deve ser configurada como um segredo no Google Colab (ou em seu ambiente de desenvolvimento).
* **Google Colab:** O código foi desenvolvido e testado no Google Colab.
* **Bibliotecas Python:** As seguintes bibliotecas Python são utilizadas e devem estar instaladas:
    * `google-genai`
    * `google-adk`
    * `requests`
    * `IPython` (para visualização no Colab)
    * `datetime`
    * `textwrap`

## Configuração

1.  **Obter a chave de API do Google Gemini:** Siga as instruções na documentação do Google Gemini para obter uma chave de API.
2.  **Configurar a chave de API no Google Colab:**
    * No seu notebook do Colab, clique em "Secrets" na barra lateral esquerda (ícone de chave).
    * Clique em "+ Add a secret".
    * No campo "Name", digite `GOOGLE_API_KEY`.
    * No campo "Value", cole sua chave de API do Google Gemini.
    * Clique em "Save".
3.  **Executar as células de instalação:** Execute as células de código no notebook para instalar as bibliotecas necessárias e configurar o ambiente.

## Como Executar

1.  Abra o notebook no Google Colab.
2.  Certifique-se de ter configurado a chave de API corretamente.
3.  Execute todas as células do notebook em ordem.
4.  O agente de extração de perfil solicitará suas informações no console. Responda às perguntas para que o sistema possa iniciar a busca de vagas.
5.  Os resultados da busca, a análise de compatibilidade e as vagas recomendadas serão exibidas no notebook.

## Observações

* Este é um projeto simplificado para demonstrar o uso dos agentes do Google ADK e da API Gemini para busca de vagas.
* A precisão e relevância das vagas encontradas dependem da qualidade das informações fornecidas pelo usuário e da eficácia das buscas realizadas pelo agente.
* O agente de compatibilidade utiliza uma lógica básica para avaliar a correspondência entre o perfil e as vagas. 
* A ferramenta de busca do Google utilizada tem suas limitações e a qualidade dos resultados pode variar.

## Próximos Passos

* Implementar uma interface de usuário mais amigável.
* Permitir o upload do currículo através de um arquivo para uma extração mais precisa do perfil da vaga
* Melhorar a lógica do agente de compatibilidade utilizando técnicas de NLP.
* Adicionar funcionalidades como salvar vagas, enviar notificações e integrar com outras plataformas de recrutamento através de APIs.
* Considerar a implementação de um sistema de feedback do usuário para refinar os resultados da busca.
