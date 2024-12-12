# automacao-ERP

## Automação ERP

Automação de ERP - Tecnobyte SAC

Descrição:
Este script realiza a automação de tarefas no ERP Tecnobyte SAC. A automação inclui:
1. Abrir o programa.
2. Realizar login.
3. Selecionar o relatório de estoque sintético.
4. Salvar o relatório no formato TXT.

Recursos utilizados:
- Reconhecimento de imagens para localizar elementos da interface (botões, ícones).
- Interação com teclado e mouse para realizar as ações necessárias.

Dependências:
- pyautogui: Para controle do mouse e teclado.
- pyperclip: Para manipulação do clipboard (caso necessário).
- subprocess: Para abrir programas externos.
- time: Para gerenciar os intervalos entre as ações.

Observações:
- Caso o mouse seja movido para uma extremidade da tela, o script será interrompido como medida de segurança (pyautogui.FAILSAFE).
- As imagens utilizadas para reconhecimento (e.g., relatorios.png, sintetico.png) devem estar no mesmo diretório do script ou especificadas corretamente no caminho.

## Importando pacotes

```
# Bibliotecas

import pyautogui
import pyperclip
import subprocess
import time
```

## Configuração de segurança:
 Permite interromper o script movendo o mouse para uma das extremidades da tela
```
pyautogui.FAILSAFE = True
```

## Função para localizar uma imagem na tela
```
def encontrar_imagem(imagem):
    while not pyautogui.locateOnScreen(imagem, grayscale=True, confidence=0.9):  # reconhecimento de imagem
        time.sleep(1)
    encontrou = pyautogui.locateOnScreen(imagem, grayscale=True, confidence=0.9)
    return encontrou
```
### Passo 1

```
# Abrir o ERP Tecnobyte Sac:
subprocess.Popen([r"C:\Tecnobyte\SAC_Free\SAC.exe"])
time.sleep(3) # Aguarda o programa abrir
```
### Passo 2
```
# Realizar login:
pyautogui.press('tab') # Navegar até o campo de senha
pyautogui.write('12345') # Digitar a senha
pyautogui.press('enter') # Confirmar o login
````
### Passo 3

```
# Navegar até o relatório desejado
pyautogui.press('enter') # Selecionar "Produtos"
time.sleep(2)   # Aguardar a próxima tela carregar

# Localizar e clicar em "Relatórios"
encontrou = encontrar_imagem('relatorios.png')
pyautogui.click(encontrou)

# Localizar e clicar em "Estoque sintético"
encontrou = encontrar_imagem('sintetico.png')
pyautogui.click(encontrou)

# Confirmar seleção do relatório
pyautogui.press('enter')  # Confirma "Estoque sintético"
pyautogui.press('enter') # Confirma "Imprimir"
time.sleep(1)
```
### Passo 4
```
# Salvar relatório
encontrou = encontrar_imagem('salvar.png')
pyautogui.click(encontrou)
time.sleep(1)
# Renomear o arquivo para "Estoque Sintetico"
pyautogui.write('Estoque Sintetico')
time.sleep(1)

# Alterar formato do arquivo para TXT
encontrou = encontrar_imagem('arquivo_pdf.png')
pyautogui.click(encontrou)
time.sleep(2)

encontrou = encontrar_imagem('arquivo_texto.png')
pyautogui.click(encontrou)
time.sleep(2)

# Confirmar o salvamento
encontrou = encontrar_imagem('salvar_arquivo_texto.png')
pyautogui.click(encontrou)
```
## Considerações finais:
- Este script pode ser adaptado para salvar arquivos em outros formatos ou locais, modificando as interações com a interface do ERP.

- Certifique-se de que as imagens utilizadas para o reconhecimento estejam atualizadas e correspondam aos elementos na tela.


