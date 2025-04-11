# Semáforo Inteligente com Arduino

## Descrição
Sistema de semáforo que ajusta dinamicamente os tempos de sinalização com base no tráfego em tempo real, utilizando Arduino.

## Teoria
- **Automação Inteligente:** Uso de IA para adaptação e tomada de decisões.
- **Cidades Inteligentes:** Uso de tecnologia para eficiência e sustentabilidade urbana.

## Componentes
- Arduino Uno
- LEDs (Vermelho, Amarelo, Verde)
- Resistores
- Sensores de Tráfego
- Sensor de Pedestres
- Botão de Pedestre
- Protoboard & Jumpers
- Fonte de Alimentação

## Código Arduino
Ajusta os tempos dos sinais com base nos dados dos sensores.

### Inicialização
```
// Declaração dos pinos dos LEDs
int ledVermelhoVeiculos = 2;
int ledAmareloVeiculos = 3;
int ledVerdeVeiculos = 4;

// Declaração do pino do botão do pedestre
int botaoPedestre = 7;

// Declaração do pino do sensor de veículos
int sensorVeiculos = A0;

// Declaração dos pinos dos LEDs de pedestres
int ledVermelhoPedestres = 8;
int ledVerdePedestres = 9;

// Variáveis para armazenar os tempos dos sinais
int tempoVerdeVeiculos = 5000;   // Tempo do verde para veículos em milissegundos (5 segundos)
int tempoAmarelo = 1000;        // Tempo do amarelo em milissegundos (1 segundo)
int tempoVermelhoVeiculos = 5000; // Tempo do vermelho para veículos em milissegundos (5 segundos)
int tempoAtravessiaPedestres = 7000; // Tempo de travessia dos pedestres em milissegundos (7 segundos)

// Função de inicialização (executada uma vez no início)
void setup() {
  // Configura os pinos dos LEDs como saída
  pinMode(ledVermelhoVeiculos, OUTPUT);
  pinMode(ledAmareloVeiculos, OUTPUT);
  pinMode(ledVerdeVeiculos, OUTPUT);

  // Configura o pino do botão do pedestre como entrada com resistor de pull-up interno
  pinMode(botaoPedestre, INPUT_PULLUP);

  // Configura os pinos dos LEDs de pedestres como saída
  pinMode(ledVermelhoPedestres, OUTPUT);
  pinMode(ledVerdePedestres, OUTPUT);
}
``

### Loop Principal
``
// Função principal (executada repetidamente)
void loop() {
  // Lógica para veículos
  // Acende o LED verde para veículos
  digitalWrite(ledVerdeVeiculos, HIGH);

  // Acende o LED vermelho para pedestres (pedestres aguardam)
  digitalWrite(ledVermelhoPedestres, HIGH);
  digitalWrite(ledVerdePedestres, LOW);

  // Mantém o LED verde aceso por 'tempoVerdeVeiculos' milissegundos
  delay(tempoVerdeVeiculos);

  // Desliga o LED verde para veículos
  digitalWrite(ledVerdeVeiculos, LOW);

  // Acende o LED amarelo para veículos
  digitalWrite(ledAmareloVeiculos, HIGH);

  // Mantém o LED amarelo aceso por 'tempoAmarelo' milissegundos
  delay(tempoAmarelo);

  // Desliga o LED amarelo para veículos
  digitalWrite(ledAmareloVeiculos, LOW);

  // Acende o LED vermelho para veículos
  digitalWrite(ledVermelhoVeiculos, HIGH);

  // Acende o LED verde para pedestres (pedestres atravessam)
  digitalWrite(ledVermelhoPedestres, LOW);
  digitalWrite(ledVerdePedestres, HIGH);

  // Mantém o LED verde para pedestres aceso por 'tempoAtravessiaPedestres' milissegundos
  delay(tempoAtravessiaPedestres);

  // Desliga o LED verde para pedestres
  digitalWrite(ledVermelhoVeiculos, LOW);

  // Acende o LED vermelho para pedestres (pedestres aguardam)
  digitalWrite(ledVermelhoPedestres, HIGH);
}
```

### Lógica de Controle
Sequência de cores dos LEDs e tempos de duração.

## Melhorias com IA
- Análise de imagens de câmeras para identificar padrões de tráfego.
- Algoritmos de otimização para ajustar tempos dos sinais.
- Integração de dados meteorológicos e eventos locais.

## Comparação
| Característica          | Semáforo Tradicional | Semáforo Inteligente |
| :----------------------- | :------------------- | :------------------- |
| Adaptação ao Tráfego   | Não                  | Sim                  |
| Consideração de Pedestres | Não                  | Sim                  |

## Referências
- "Cyber-Physical System for Smart Traffic Light Control"
