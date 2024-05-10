# A first-level heading # 👋 MIPA - Chatbot de Etiqueta Social para Neuroatípicos 🧠

# Índice

*Descrição do Projeto
*Status do Projeto
*Funcionalidades e Demonstração da Aplicação
*Acesso ao Projeto
*Tecnologias utilizadas
*Pessoas Contribuidoras
*Pessoas Desenvolvedoras do Projeto
*Licença
*Conclusão

# Descrição do Projeto
MIPA é um chatbot inovador projetado para auxiliar neuroatípicos nas interações sociais, fornecendo orientações claras e amigáveis sobre as regras de etiqueta social. 🧠🗣️
Através de uma interface conversacional intuitiva, a MIPA responde a perguntas, oferece dicas e exemplos práticos para diversas situações sociais, ajudando os usuários a navegar com mais confiança e naturalidade no mundo social. 🤝

# Status do Projeto
🚧 Em Desenvolvimento
O projeto MIPA está em fase inicial de desenvolvimento, com funcionalidades básicas implementadas. Estamos trabalhando continuamente para expandir suas capacidades e aprimorar a experiência do usuário.

# Funcionalidades e Demonstração da Aplicação
**Funcionalidades Atuais:**
O chatbot responde a perguntas sobre regras de etiqueta social.
Fornece exemplos práticos de como se comportar em diferentes situações sociais.
Utiliza o modelo de linguagem Google Gemini para gerar respostas informativas e contextualmente relevantes.

# Acesso ao Projeto
🛠️ O código fonte do projeto está disponível neste repositório GitHub .
https://github.com/TharciliaRR/MIPA/blob/cb4816787cc5d98d7e2f600aa2498f1003b1d5ea/MIPA.ipynb

# Tecnologias utilizadas
**Python: Linguagem de programação principal.**
**Google Gemini: Modelo de linguagem avançado para geração de texto.**
**Google Colab: Ambiente de desenvolvimento utilizado para o projeto.**

# Pessoas Contribuidoras
[https://www.linkedin.com/in/tharciliarollemberg/]
# Pessoas Desenvolvedoras do Projeto
[https://www.linkedin.com/in/tharciliarollemberg]
# Licença
Este projeto está licenciado sob a licença gratuita do GOOGLE.

# Conclusão
O projeto MIPA tem como objetivo promover a inclusão social de neuroatípicos, empoderando-os com as ferramentas necessárias para navegar com segurança e confiança nas interações sociais.
Acreditamos que este projeto tem o potencial de gerar um impacto positivo na vida de muitas pessoas, contribuindo para um mundo mais inclusivo e compreensivo. 🌎❤️
Convidamos você a se juntar a nós nesta missão! 🙏

# Código do Projeto

**INSTALAÇÃO** 

#Instalando o SDK do Google
!pip install -q -U google-generativeai


**Configurações iniciais**


import google.generativeai as genai
from google.colab import userdata
api_key= userdata.get('SECRET_KEY')
genai.configure(api_key=api_key)

generation_config = {
  "candidate_count": 1,
  "temperature": 0.5,
}

safety_settings={
    'HATE': 'BLOCK_NONE',
    'HARASSMENT': 'BLOCK_NONE',
    'SEXUAL' : 'BLOCK_NONE',
    'DANGEROUS' : 'BLOCK_NONE'
    }

model = genai.GenerativeModel(model_name='gemini-1.0-pro',
                                  generation_config=generation_config,
                                  safety_settings=safety_settings,)


**Iniciando o chat**


chat = model.start_chat(history=[])

**Melhorando a visualização**


#código disponível em https://ai.google.dev/tutorials/python_quickistart#import_packages
import textwrap
from IPython.display import display
from IPython.display import Markdown

def to_markdown(text):
   text = text.replace('...', ' ')
  return Markdown(textwrap.indent(text, '> ', predicate=lambda _: True))

#Imprimindo o histórico
for message in chat.history:

                  display(to_markdown(f"**{message.role}**: {(message.parts[0]).text}"))
  print('___________________________________')

  

**Loop de interação**


prompt = input('OLá! Sou a MIPA como posso te ajudar:')
while prompt != "xau":
  response = chat.send_message(prompt)
  resposta_bot = gerar_resposta(response.text)
  print("Resposta:", response.text, "\n")
prompt = input('Esperando prompt: ')



