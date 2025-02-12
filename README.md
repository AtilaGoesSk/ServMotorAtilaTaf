# Controle de Servo Motor e LED RGB com Raspberry Pi Pico W

## Descrição do Projeto
Este projeto utiliza a placa **Raspberry Pi Pico W** para controlar um **servo motor** e um **LED RGB** da BitDogLab. O servo motor realiza um movimento oscilante entre 0° e 180° de forma suave, enquanto o LED muda de estado conforme o movimento do servo.

O controle é feito utilizando **PWM (Pulse Width Modulation)** para movimentar o servo motor em diferentes posições, e um sinal digital simples para ligar e desligar o LED.

## Componentes Necessários
- **Raspberry Pi Pico W**
- **Servo Motor** (compatível com PWM de 50Hz)
- **LED RGB BitDogLab**
- **Jumpers** para conexões
- **Fonte de alimentação (5V)** para o servo motor (caso necessário)

## Esquema de Ligação
| Componente  | Pino Raspberry Pi Pico W |
|-------------|--------------------------|
| Servo Motor | GPIO 22 (PWM)            |
| LED RGB     | GPIO 12                   |
| VCC (5V)    | VSYS (5V)                 |
| GND         | GND                        |

## Configuração do Ambiente
Antes de compilar e rodar o projeto, certifique-se de ter instalado:
- **SDK do Raspberry Pi Pico**
- **Compilador ARM (arm-none-eabi-gcc)**
- **CMake e Make**

### 1. Clonar o Repositório (caso aplicável)
```sh
    git clone https://github.com/seu_usuario/seu_projeto.git
    cd seu_projeto
```

### 2. Compilar o Código
```sh
    mkdir build
    cd build
    cmake ..
    make -j4
```

### 3. Carregar o Arquivo na Raspberry Pi Pico W
1. Conecte a placa segurando o botão **BOOTSEL**.
2. Solte o botão e um disco chamado **RPI-RP2** irá aparecer.
3. Arraste e solte o arquivo **.uf2** gerado na pasta `build`.

## Funcionamento do Código
- Inicializa a comunicação serial e configura os pinos GPIO.
- Configura o **PWM** para controlar o servo motor.
- Movimenta o servo para **180°**, depois para **90°**, e por fim para **0°**.
- Em seguida, faz uma movimentação cíclica suave entre **0° e 180°**, alternando o estado do LED.

## Manual de Uso
### 1. Alimentação e Conexão
- Conecte o **servo motor** e o **LED RGB** nos pinos correspondentes da Raspberry Pi Pico W.
- Conecte a Pico W a um computador via **USB-C**.
- Siga o processo de compilação e upload do código.

### 2. Teste e Operação
- Assim que o código iniciar, o servo irá realizar movimentos de calibração.
- O LED RGB piscará conforme a movimentação do servo.
- O movimento do servo será oscilante entre **0° e 180°** de forma suave.

### 3. Ajustes e Modificações
- **Velocidade do Movimento:** Modifique `STEP_SIZE` e `STEP_DELAY` no código.
- **Posições do Servo:** Alterar `SERVO_0`, `SERVO_90` e `SERVO_180`.
- **LED RGB:** Modificar `gpio_put(LED_PIN, estado);` para mudar a lógica do LED.

## Possíveis Erros e Soluções
| Erro | Causa Possível | Solução |
|------|---------------|---------|
| Servo não se move | PWM não configurado corretamente | Verifique as definições de `PWM_WRAP` e `CLOCK_DIV` |
| LED não acende | Pino errado ou defeito | Verifique as conexões e use um multímetro |
| Arquivo `.uf2` não carrega | Placa não no modo BOOTSEL | Reconecte segurando o botão BOOTSEL |

## Autor
**Átila Goes** - Desenvolvedor de Software e entusiasta de projetos com Raspberry Pi Pico W.

---
Se tiver dúvidas ou quiser contribuir, entre em contato pelo e-mail: atilagoes.tech@gmail.com 🚀

