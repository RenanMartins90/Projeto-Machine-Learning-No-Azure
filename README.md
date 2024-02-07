# Machine Learning no Azure ML

Trabalhando com Machine Learning na Prática no Azure ML da DIO.

Links importantes:

[Explore Azure AI Services](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/02-content-safety.html)

[Explore Automated Machine Learning in Azure Machine Learning](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html)

[Fonte dos dados](https://aka.ms/bike-rentals)

## Passo 1: Criação do recurso Azure Machine Learning

Crei um recurso de Machine Learning. Para isso, cliquei em "Criar recurso" e depois pesquisei por Azure Machine Learning no marketplace.

![Img](./imgs/img1.gif)

## Passo 2: Configurando o recurso do Azure Machine Learning

Na aba de Noções básica, Detalhes do recurso, informei a assinatura para cobrança no campo Assinatura e logo após informei o Grupo de recursos que vai englobar o recurso que será criado.

Após, em Detalhes da área de trabalho, informei os detalhes do workspace que será criado. Por último, criei o recurso clicando em Consultar + criar. Após a validação ser aprovada, cliquei em "Criar".

![Img](./imgs/img2.png)

Após o recurso criado, cliquei no botão "Ir para o recurso" para acessar a página do recurso.

![Img](./imgs/img3.png)

Nesta página, existe o botão "Iniciar o estúdio" que redirecionará para o estúdio do Azure Machine Learning.

![Img](./imgs/img4.png)

## Passo 3

No estúdio, na página do workspace criado anteriormente, acessei a opção do menu ML automatizado e na página aberto, cliquei em "Novo trabalho de ML automatizado".

![Img](./imgs/img5.gif)

Em "Configurações básicas", preenchi os campos "Nome do trabalho", "Novo nome do experimento" e "Descrição". 

No passo "Tipo de tarefa e dados", selecionei o tipo de tarefa como Regressão e em seguida, em "Selecionar dados", cliquei em "Criar". No modal aberto, em "Tipos de dados", preenchi os campos "Nome", "Descrição" e escolhi "Tipo" como Tabular. Cliquei em "Avançar" e no passo "Fonte de dados", escolhi "De arquivos da Web" e cliquei em avançar novamente.

No passo "URL da Web", informei a URL https://aka.ms/bike-rentals do conjunto de dados. No passo "Configurações", preenchi as configurações do conjunto e após avançar para "Esquema", verifiquei os tipos de dados. Verifiquei as configurações criadas para o ativo de dados e cliquei em criar.

![Img](./imgs/img6.gif)

Em "Configurações de tarefas", escolhi o conjunto de dados importado. Após, em "Coluna de destino" escolhi a coluna rentals como target.

Nos campos de "Limite", preenchi com os valores abaixo e marquei "habilitar encerramento antecipado".

![Img](./imgs/img7.png)

Em "Validar e testar", em "Tipo de validação" escolhi "Divisão de validação de treinamento".

Ao avançar, em Computação, mantive os valores mostrados na imagem abaixo.

![Img](./imgs/img8.png)

Após avançar e examinar as configurações do trabalho, cliquei em "Enviar trabalho de treinamento".

Após finalizar o trabalho de treinamento, o modelo fica acessível na opção de menu "Modelo".

![Img](./imgs/img9.png)

## Passo 4: As métricas do modelo

Para acessar as métricas do modelo treinado, na página do modelo, acesso o link informado em "Criado por trabalho". 

![Img](./imgs/img10.gif)

## Passo 5: O teste do modelo

Na página do modelo, cliquei na aba "Pontos de extremidade". Também é possível acessar pelo menu lateral em "Pontos de extremidade". Cliquei no ponto correspondente ao modelo gerado. Em seguida, acessei a aba "Testar".

Para o teste, utilizei o .json abaixo:

<code>
{
  "input_data": {
    "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]
  }
}
</code>

A previsão gerada foi de: 361.95

![Img](./imgs/img11.png)
