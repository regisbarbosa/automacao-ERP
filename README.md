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
- pandas (opcional): Não está sendo usado no momento, mas foi importado.

Observações:
- Caso o mouse seja movido para uma extremidade da tela, o script será interrompido como medida de segurança (pyautogui.FAILSAFE).
- As imagens utilizadas para reconhecimento (e.g., relatorios.png, sintetico.png) devem estar no mesmo diretório do script ou especificadas corretamente no caminho.
