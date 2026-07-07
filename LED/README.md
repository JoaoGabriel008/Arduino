# Led

Em algum momento do seu dia, certamente você teve de ligar algum aparelho eletrônico e para notar que estava funcionando, observou o acender de uma “luz”. Esta “luz” trata-se do “**LED**”. Agora, você já se perguntou como ele funciona? E quais são as suas utilidades? 

Então, iremos juntos entender um pouco mais a respeito desse componente eletrônico que nos rodeia no mundo atual.

<div align="center">
<h3>Figura 1: LED verde </h3>	
<img width="1263" height="545" alt="Image" src="https://github.com/user-attachments/assets/51263185-0ae2-40e7-b2e6-5268894e8a32"/>
<h4>Fonte: Olhar digital </h4>
</div>

# O que é o LED?

Para começarmos a decifrar esse componente, primeiramente precisaremos entender o significado de seu nome. Os “LEDs”, ou **Diodos Emissores de Luz**(Light Emitting Diodes), são dispositivos semicondutores que convertem **energia elétrica** em **luz visível**. 

São especialmente utilizados em produtos de **microeletrônica** como sinalizador de avisos, também podem ser encontrados em tamanho maior, como em alguns modelos de semáforos. Além disso, o led é amplamente utilizado em painéis, cortinas, pistas e postes de iluminação pública, contribuindo para uma redução significativa no consumo de energia elétrica. 

# Estrutura do LED

<div align="center">
<h3>Figura 2: Estrutura do LED </h3>	
<img width="1263" height="545" alt="Image" src="https://github.com/user-attachments/assets/c3252dce-9d22-48eb-b041-5585c3f02cbc" />
<h4>Fonte: Wikipédia </h4>
</div>

A estrutura de um LED , como está na Figura 2, é composta por um **ânodo (terminal positivo)** e um **cátodo (terminal negativo)**, entre os quais está localizada uma junção semicondutora (interface onde dois materiais semicondutores com propriedades elétricas opostas se encontram).

# Funcionamento do LED

Os LEDs funcionam por meio da **eletroluminescência**, que é a emissão de luz quando uma corrente elétrica passa por um material semicondutor. Um “LED” possui duas camadas de material semicondutor: uma do tipo **p** (positiva) e outra do tipo **n** (negativa). Quando uma tensão elétrica é aplicada, os elétrons se movimentam e encontram as lacunas na junção entre essas camadas.

<div align="center">
<h3>Figura 3: Funcionamento do LED </h3>	
<img width="1263" height="545" alt="Image" src="https://github.com/user-attachments/assets/74354624-f65c-4574-8d23-3f07f8dee9bf" />
<h4>Fonte: Google </h4>
</div>

Quando elétrons e lacunas se encontram, eles se recombinam e liberam energia na forma de luz. Essa luz é formada por pequenas partículas chamadas **fótons**. A cor da luz emitida pelo “LED” depende do material utilizado em sua fabricação. Cada material libera uma quantidade diferente de energia, produzindo cores diferentes, como vermelho, verde, azul ou branco.

<div align="center">
<h3>Figura 4: LEDs coloridos </h3>	
<img width="1263" height="545" alt="Image" src="https://github.com/user-attachments/assets/74bfac0e-e709-465d-bb2a-bc820b6d889f" />
<h4>Fonte: Google </h4>
</div>

# Simulação

Agora que compreendemos melhor sobre o “LED” e seu funcionamento, vamos juntos ver na prática como podemos aplicá-lo em um **arduino** (uma plataforma para criar projetos eletrônicos, com hardware e software fáceis de usar) e criar um contador binário. Mas antes de começar, primeiramente precisamos separar os materiais necessários para a montagem do circuito. Aqui vai a lista:  

# Lista de Materias:

- 3 LEDs;
- 3 Resistores de 220 Ω;
- 5 Jumper;
- 1 protoboard(Placa de ensaio);
- 1 arduino;


Para essa simulação, estaremos utilizando o **Tinkercad**, uma ferramenta virtual que possibilita a criação de protótipos de arduínos sem a necessidade de possuí-los fisicamente. É uma ótima maneira de criar modelos 3D, simular circuitos eletrônicos e programar microcontroladores. 

<div align="center">
<h3>Figura 5: Contador binário com LED </h3>	
<img width="1263" height="545" alt="Image" src="https://github.com/user-attachments/assets/bec75950-b2e2-43a7-adb7-ea2843173268" />
<h4>Fonte: Autoria própria </h4>
</div>

Agora, com o material separado, faça as conexões entre o Arduino e a protoboard conforme a Figura 5. Conecte o pino “**GND**” (terra) do Arduino ao barramento negativo da protoboard. Em seguida, ligue cada LED ao respectivo pino digital do Arduino por meio de um **resistor**, mantendo o **ânodo** do LED conectado ao resistor e o **cátodo** ao “**GND**”. Organize os cabos utilizando cores diferentes para facilitar a identificação das conexões e a correção de possíveis erros durante a montagem. 

# Código 

Após montado, partimos para a construção do código. E é aqui, onde daremos vida ao nosso contador. Por isso, fique atento aos detalhes!

Primeiro, definimos as variáveis que iremos utilizar e atribuímos a portal digital de saída do arduíno:

```cpp
int led1 = 2;
int led2 = 3;
int led3 = 4;
```
Em seguida, iremos para a função ‘void setup()’, onde ela é executada somente uma vez assim que a placa é ligada ou reiniciada, servindo para preparar o sistema antes do código principal rodar. 

```cpp
void setup() {
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}
```
Aqui, atribuímos as nossas variáveis à função ‘pinMode’, que será um comando essencial para configurar um pino específico funcionar como saída (enviando sinais) com o modo “**OUTPUT**”. 

Partindo para a função ‘void loop()’, iremos inserir o código principal que será executado repetidamente em ciclo contínuo. Começando com um laço de repetição: 

```cpp
for (int num = 0; num < 8; num++) {
```
O programa vai fazer uma contagem de um valor que inicia no 0 e repete acrescentando 1 enquanto seu valor for menor que 8. Ou seja, o código dentro do “**for**” vai rodar 8 vezes (0, 1, 2, 3, 4, 5, 6, 7).

Neste momento, estamos entrando em contato com a linguagem nativa dos computadores, através da utilização de Bits que trata-se do menor unidade de informação que um computador pode armazenar e processar, podendo assumir apenas dois estados: 0 ou 1.

```cpp
    int b0 = num % 2;       
    int b1 = (num / 2) % 2;  
    int b2 = (num / 4) % 2;
```
 Cada uma dessas variáveis representa um bit do número armazenado em um ‘num’. Como cada bit só pode assumir os valores de 0 ou 1, o programa separa o número decimal em sua forma binária, identificando quais posições devem ficar ligadas ou desligadas. Nesse caso, ‘b0’ corresponde ao bit de valor 1, ‘b1’ ao bit de valor 2 e ‘b2’ ao bit de valor 4. Assim, os LEDs podem representar os números de 0 a 7, de acordo com a combinação binária formada. 

 Com isso:

- b0 - Pega o bit da direita do número
- b1 - Pega o bit do meio (primeiro divide por 2, depois pega o resto da divisão por 2)
- b2 - Pega o bit da esquerda (primeiro divide por 4, depois pega o resto da divisão por 2)

Assim, chegando a penúltima função, o ‘digitalWrite()’ que serve para enviar um sinal elétrico (nível lógico) para um pino digital. Ele vai ligar ou desligar o LED de acordo com a variável:

```cpp
    digitalWrite(led1, b0);
    digitalWrite(led2, b1);
    digitalWrite(led3, b2); 
```

Finalizando com a função ‘delay()’ que vai adicionar a espera de 1 segundo antes de mostrar o próximo número.

```cpp
delay(1000);
```

Desta forma, concluímos nossa simulação de um contador binário utilizando os LEDs para representá-los. Essa é apenas uma das várias maneiras de aplicar o LED, que faz parte de algum aparelho eletrônico perto de você!

Linkd do circuito no tinkercad: https://www.tinkercad.com/things/eCV0aHjajZD-contador-binario-com-3-leds?sharecode=0NC4vcAwEU4mD_MbRB6D_NJwfa2_0fMpkx3NTu2iYyw

- <p><a href="https://github.com/JoaoGabriel008"> João Gabriel</a></p>

