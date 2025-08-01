# README - classificador-frames-video
## Visão Geral
### Este projeto implementa uma solução completa para análise de vídeo, incluindo:

- Separação de áudio e vídeo
- Extração e armazenamento de frames
- Processamento e análise de imagens
- Classificação de objetos usando Machine Learning
- Transcrição de áudio

# Requisitos
Python 3.9+

Bibliotecas listadas em requirements.txt

# Instalação
1. Clone o repositório:
```bash

git clone https://github.com/MarceloHorikoshi/classificador-frames-video.git
cd classificador-frames-video
```
2. Instale as dependências:
```bash

pip install -r requirements.txt
```
3. BAIXE O VÍDEO.
  - Estou disponibilizando o vídeo que foi utilizado no projeto nesta url [loveletter_bananagrams_caneca.mp4](https://drive.google.com/file/d/1pjKg0DHtc2RHSt25roMVOR5Et2mgfqYn/view?usp=sharing)
  - Coloque o vídeo na mesma estrutura descrita a baixo, dentro da pasta ```data/```
  
4. Baixe ou instale o pacote ffmpeg:
   - No MacOS eu baixei os pacotes [ffmpeg-7.1.1](https://evermeet.cx/ffmpeg/ffmpeg-7.1.1.zip) e 
[ffprobe-7.1.1](https://evermeet.cx/ffmpeg/ffprobe-7.1.1.zip) e extrai os zips para dentro de uma pasta chamada ffmpeg

- Não utilizar os comandos abaixo em ambientes que não forem MacOS;
```
! xattr -d com.apple.quarantine ffmpeg/ffmpeg
! xattr -d com.apple.quarantine ffmpeg/ffprobe
```

# Estrutura do projeto

```
data/
  ├── audio.mp3                 # Áudio extraído
  ├── bounding_box_images/      # Imagens com bounding boxes
  ├── db_sqlite/                # Banco de dados SQLite
  ├── histogram_analysis/       # Análises de histograma
  ├── loveletter_bananagrams_caneca.mp4  # Vídeo original
  ├── transcricao_audio/        # Transcrição de áudio
  └── video_sem_audio.mp4       # Vídeo sem áudio

models/
  ├── best_model.pkl            # Modelo treinado
  └── scaler.pkl                # Scaler para normalização

ffmpeg/                         # Binários do FFmpeg
```

# Fluxo de Processamento

1. Separação do Aúdio e Vídeo:
   - Extrai áudio do vídeo original;
   - Salva vídeo sem áudio; <br/>
   

2. Processamento de Vídeo:
   - Extrai frames em intervalos regulares;
   - Armazena frames em banco SQLite com metadados;
   - Aplica técnicas de processamento de imagem (CLAHE, equalização) <br/>


3. Classificação de Objetos:
   - Extrai features dos frames;
   - Aplica algoritmos de clustering (K-Means);
   - Treina modelos de classificação (Random Forest, SVM);
   - Detecta e classifica objetos nos frames; <br/>


4. Processamento de Áudio:
   - Converte áudio para formato WAV;
   - Transcreve usando Google Speech Recognition;
   - Salva transcrição em arquivo de texto.<br/>

# Como Executar

1. Certifique-se que o arquivo ***loveletter_bananagrams_caneca.mp4*** esteja na pasta ```data/```;
2. Execute o notebook Jupyter ```main.ipynb``` célula por célula.
3. Certifique-se que o banco de dados foi criado corretamente na pasta ```data/db_sqlite```

# Resultados Esperados

- Vídeo sem aúdio (``video_sem_audio.mp4``);
- Áudio extraído (``audio.mp3``);
- Banco de dados SQLite com tabela chamada ``video_frames`` com frames e metadados;
- Modelo (``best_model.pkl ``) e Scaler (``scaler.pkl ``);
- Geração de gráficos de PCA, t-SNE, Gráficos de melhores features e Matriz de confusão;
- Imagens com bounding boxes dos objetos detectados;
- Arquivo de texto com a transcrição do áudio.

# Observações
- O projeto foi desenvolvido e testado em ambiente macOS;
- Para Executar é necessário a pasta ffmpeg para captura e processamento de arquivos de audio, principalmente para 
conversão para o formato WAV para a transcrição;
- Para outros sistemas operacionais, pode ser necessário ajustar o caminho do FFmpeg


Autor
Marcelo Horikoshi Candido da Silva
