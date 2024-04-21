# Meeting Summary with OpenAI
Desenvolvido por: Valentim Uliana

Essa aplicação tem como intuito a facilitação no dia-dia de quem faz muitas reuniões, onde a partir de uma gravação de reunião, é possível gerar um resumo usando o ChatGPT e trazer tudo que foi acordado numa reunião, desde tópicos abordados até  próximos passos.

# Requisitos
   Python(3.8+) com Streamlit<br>
   Testado com sistema operacional Windows 11 e Linux Ubuntu 20.0 <br>
   <a href="https://ffmpeg.org/">FFMPEG </a>: Uma solução completa e multiplataforma para gravar, converter e transmitir áudio e vídeo.<br>
   <a href="https://alphacephei.com/vosk/">VOSK </a>: Ferramenta para reconhecimento de fala offline, pois suporta PT-BR muito bem e não é preciso pagar alguma API.<br>
   <a href="https://platform.openai.com/docs/introduction">OpenAI </a>: Utilizado a API do OpenAI para fazer o resumo das reuniões (aqui é pago, por exemplo, eu utilizei $5 e já upei mais de 50 reuniões e ainda tenho créditos)<br>
   Use: <b>pip install -r requirements.txt</b> para instalar as bibliotecas necessárias<br>

# Como utilizar
1. Primeiramente pegar o consentimento para gravar uma reunião
2. A aplicação foi feita em Python utilizando o streamlit, então para iniciá-la basta rodar o comando (depende do IDE e sistema operacional que vc irá utilizar) : <b>```streamlit run .\meeting_summarizer_openai.py --server.maxUploadSize 700```</b>
3. Basta upar a reunião (aceita por enquanto somente arquivos .mp4) e clicar em gerar resumo.
4. A aplicação vai transformar o MP4 em áudio, transcrever esse aúdio para texto usando o VOSK e com esse texto mandar para um prompt do OpenAI para fazer um resumo com as pré-definições que eu fiz na linha 18 do código (pode ser alterado de acordo com cada necessidade)
   ```
   PROMPT = '''
      Somos da empresa Yssy, empresa de tecnologia que atende diversas frentes.
      Faça o resumo do texto delimitado por #### 
      O texto é a transcrição de uma reunião.
      Tente identificar se foi citado nesse texto de algum cliente e colocar no nome dele.
      Se houver alguma data definida para alguma atividade ou próxima reuniao, colocar essa data no formato dd/MM/aaaa
      O resumo deve contar com os principais assuntos abordados e separados por topico e bem detalhado.
      O resumo deve estar em texto corrido.
      O resumo deve contar com as soluções tecnologicas proposta.
      No final, devem ser apresentados todos acordos,combinados e proximos passos
      feitos na reunião no formato de bullet points.
      
      O formato final que eu desejo é:
      
      Resumo reunião:
      - escrever aqui o resumo detalhado
      
      Nome do cliente:
      - escrever aqui o nome do cliente se foi identificado
      
      Acordos da Reunião :
      - acordo 1
      - acordo 2
      - acordo 3
      - acordo n
      
      Próximos passos :
      - passo 1
      - passo 2
      - passo n
      
      
      Soluções propostas:
      - solução 1
      - solução 2
      - solução n
      
      Data próximos passos ou reuinão:
      - escrever aqui a data
      
      texto: ####{}####
      '''
   ```
5. Após a reunião tiver um resumo pronto, ele vai para a TAB <b>"Ver Resumos de reuniões"</b> onde você deve salvar o título da reunião dando um nome para ela. Após isso a reunião vai aparecer para você já resumida.
