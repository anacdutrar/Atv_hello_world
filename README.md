# Atv_hello_world

Projeto de exemplo para ESP32-S3 que executa um modelo TensorFlow Lite Micro
quantizado. O firmware alimenta o modelo com valores de entrada, realiza uma
inferência a cada 500 ms e imprime os valores de entrada e saída no monitor
serial.

## Tecnologias

- ESP-IDF 5.1 ou mais recente (o projeto foi compilado com ESP-IDF 6.1.0)
- ESP32-S3
- TensorFlow Lite Micro para ESP-IDF
- Wokwi para simulação opcional

## Estrutura principal

- `main/`: código-fonte e modelo convertido em um array C++
- `hello_world_int8.tflite`: modelo TensorFlow Lite quantizado original
- `main/idf_component.yml`: dependência do TensorFlow Lite Micro
- `dependencies.lock`: versões resolvidas das dependências
- `diagram.json` e `wokwi.toml`: configuração da simulação no Wokwi
- `.devcontainer/`: ambiente de desenvolvimento opcional em contêiner

As pastas `build/` e `managed_components/` são geradas automaticamente e não
são versionadas.

## Compilar e executar

Com o ambiente do ESP-IDF configurado:

```bash
idf.py set-target esp32s3
idf.py build
idf.py -p PORTA flash monitor
```

Substitua `PORTA` pela porta serial da placa, por exemplo `COM3` no Windows ou
`/dev/ttyUSB0` no Linux. Para sair do monitor serial, use `Ctrl+]`.

Na primeira compilação, o ESP-IDF baixa os componentes declarados em
`main/idf_component.yml` e recria `managed_components/`.

## Simular no Wokwi

Compile o projeto primeiro com `idf.py build`. Depois, abra o projeto com a
extensão Wokwi para VS Code; ela utilizará `diagram.json` e `wokwi.toml`.
