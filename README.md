# Arduino WWVB & JJY Transmitter

02/05/2017 - Tx example now working! But its kinda useless as no sync examples are provided yet (put it in my TODO list)

An Arduino based WWVB & JJY transmitter for ATmega328p and ATmega32u4 based Arduino boards
Works with 16MHz or 8MHz boards

* Author/s: [Mark Cooke](https://www.github.com/micooke), [Martin Sniedze](https://www.github.com/mr-sneezy)
* @micooke : Software
* @mr-sneezy : Hardware

## Requirements
* [Time.h - standard Arduino library](http://www.arduino.cc/playground/Code/Time)
* [PWM.h](https://github.com/micooke/PWM/PWM.h)
* [Timezone.h](https://github.com/JChristensen/Timezone)

## Implementation notes
Note: the following `#define`'s must come in your .ino file prior to including [wwvb_jjy.h] (https://github.com/micooke/wwvb_jjy/blob/master/wwvb_jjy.h)
* Normally the inbuilt LED is flashed along with the modulation. `#define WWVB_JJY_PULSE_LED 0` will disable it
* `#define WWVB_JJY_PWM` : PAM method outputs a CW carrier and a modulation signal on two separate pins
* (default) : PWM method sets the duty cycle of the carrier to 0 for signal low. the modulation signal is still output (incase you want a blinky light?)

## About WWVB
http://www.nist.gov/pml/div688/grp40/wwvb.cfm

WWVB: 60kHz carrier, Amplitude modulated to Vp -17dB for signal low


## About JJY
http://jjy.nict.go.jp/jjy/trans/index-e.html

JJY: 40kHz carrier, Amplitude modulated to Vp -17dB for signal low (same as WWVB)

JJY is inverted compared to WWVB. At the start of a pulse it is HIGH (WWVB starts low) and the time at which it goes LOW determines the code type.

As explained in : https://en.wikipedia.org/wiki/JJY
> There are three different signals that are sent each second:
> * 0 bits consist of 0.8 s of full power, followed by 0.2 s of reduced power.
> * 1 bits consist of 0.5 s of full power, followed by 0.5 s of reduced power.
> * Marker bits consist of 0.2 s of full power, followed by 0.8 s of reduced power.

## Hookup

![wwvb wiring options](wwvb_bb.png?raw=true)

* Tx example - static time set, non-syncing examples
* Rx example - receives the modulation pin to decode your timecode for debug purposes

---

Segue abaixo a tradução completa e fiel do conteúdo do arquivo `README.md` para o português do Brasil:

---

# Transmissor WWVB & JJY com Arduino

02/05/2017 - Exemplo de transmissão agora funcionando! Mas é meio inútil, já que ainda não há exemplos de sincronização disponíveis (coloquei isso na minha lista de tarefas)

Um transmissor WWVB & JJY baseado em Arduino para placas Arduino com ATmega328p e ATmega32u4  
Funciona com placas de 16 MHz ou 8 MHz

* Autor(es): [Mark Cooke](https://www.github.com/micooke), [Martin Sniedze](https://www.github.com/mr-sneezy)  
* @micooke : Software  
* @mr-sneezy : Hardware  

## Requisitos
* [Time.h - biblioteca padrão do Arduino](http://www.arduino.cc/playground/Code/Time)  
* [PWM.h](https://github.com/micooke/PWM/PWM.h)  
* [Timezone.h](https://github.com/JChristensen/Timezone)  

## Notas de implementação
Nota: os seguintes `#define` devem ser inseridos no seu arquivo `.ino` antes de incluir [wwvb_jjy.h](https://github.com/micooke/wwvb_jjy/blob/master/wwvb_jjy.h)  
* Normalmente o LED embutido pisca junto com a modulação. `#define WWVB_JJY_PULSE_LED 0` irá desativá-lo  
* `#define WWVB_JJY_PWM` : o método PAM emite uma portadora CW e um sinal de modulação em dois pinos separados  
* (padrão): o método PWM define o ciclo de trabalho da portadora como 0 para sinal baixo. o sinal de modulação ainda é emitido (caso você queira uma luz piscando?)  

## Sobre o WWVB  
http://www.nist.gov/pml/div688/grp40/wwvb.cfm  

WWVB: portadora de 60 kHz, modulada em amplitude para Vp -17 dB para sinal baixo  

## Sobre o JJY  
http://jjy.nict.go.jp/jjy/trans/index-e.html  

JJY: portadora de 40 kHz, modulada em amplitude para Vp -17 dB para sinal baixo (igual ao WWVB)  

JJY é invertido em relação ao WWVB. No início de um pulso, ele está ALTO (WWVB começa baixo) e o momento em que ele vai para BAIXO determina o tipo de código.

Conforme explicado em: https://en.wikipedia.org/wiki/JJY  
> Três sinais diferentes são enviados a cada segundo:  
> * Bits 0 consistem em 0,8 s em potência total, seguidos por 0,2 s em potência reduzida.  
> * Bits 1 consistem em 0,5 s em potência total, seguidos por 0,5 s em potência reduzida.  
> * Bits marcadores consistem em 0,2 s em potência total, seguidos por 0,8 s em potência reduzida.  

## Conexões

![opções de conexão do wwvb](wwvb_bb.png?raw=true)

* Exemplo de Tx - tempo estático definido, exemplos sem sincronização  
* Exemplo de Rx - recebe o pino de modulação para decodificar seu código de tempo para fins de depuração  

---
