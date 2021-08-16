Com o intuito de fazer a aplicação funcionar, os seguintes comandos devem ser executados: 

(OS Linux)
	
	sudo apt-get install buil-essential cmake pkg-confi
	sudo apt install python-pip
	pip3 install dlib --verbose
	pip3 install scikit-learn
	pip3 install --upgrade imutils
	pip3 install opencv-contrib-python
	pip3 install tensorflow
	
(OS Windows)
	
	pip install cmake
	pip install dlib
	pip install face_recognition
	pip install opencv-contrib-python
	pip install imutils
	pip install requests
	pip install tensorflow
	pip install keras
	pip install SKLearn 
	
	
No diretório "root" da aplicação, temos 6 arquivos. Sendo eles:

search_bing_api.py: 
        
     Fazendo uso do bing como método de pesquisa, este arquivo ".py" recebe duas entradas ao ser executado, 
     sendo a primeira o que se deseja pesquisar (imagens) e o segundo o diretório onde serão inseridas as 
     imagens pesquisadas. OBS: Necessário uma API da microsoft, sendo possível requisitar 7 dias grátis.
    
encode_faces.py: 	
    
    Codificação de imagens em 128-d vetores são construídas com este script. Propósito: preparar as 
    imagens para o treinamento do software.

recognize_faces_image.py:
        
    Reconhecimento de faces em uma imagem, tendo como base imagens dentro da pasta "dataset".

recognize_faces_video.py: 

    Reconhecimento de faces em um vídeo, ou a partir de uma webcam.

recognize_faces_video_file.py: 

    Reconhecimento de faces em um video em disco, com saída processada do video também em disco. 
    O funcionamento deste arquivo ".py" se assemelha com o arquivo "recognize_faces_video.py".

encodings.pickle: 

    Códificação das faces são geradas, tendo como insumo os arquivos (imagens) presentes
    na pasta "dataset", através do "encode_faces.py", sendo então serializados em disco.
		
---------------------------------------------------------------------------------------------------------------------

The dlib library, maintained by Davis King, contains our implementation of “deep metric learning” which is used to construct our face embeddings used for the actual recognition process.

The face_recognition  library, created by Adam Geitgey, wraps around dlib’s facial recognition functionality, making it easier to work with.

---------------------------------------------------------------------------------------------------------------------

Ordem de execução:

0 - search_bing_api.py (Opcional) -> Busca automatica das imagens 
	
	0.1 usage: search_bing_api.py [-h] -q QUERY -o OUTPUT
	
	0.2 	--query ="search query to search Bing Image API for")
		--output ="path to output directory of images")
		
	obs.: é preciso ter uma conta paga no Azure, e inserir no código a sua chave.
	![image](https://user-images.githubusercontent.com/52551449/129500065-b8d4e27c-99f6-4104-b40b-63e3de15aca6.png)


1 - python encode_faces.py  -> Script para realizar a codificação dos rostos presentes nas imagens em vetores (128-d face embeddings).

2 - recognize_faces_image.py 
