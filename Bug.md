# Casos Clássicos de Bugs em Software: Impactos Históricos na Sociedade

A história da engenharia de software é marcada por inovações incríveis, mas também por falhas catastróficas. Quando sistemas críticos não são devidamente testados e validados, os "bugs" podem transcender a tela do computador e causar enormes prejuízos financeiros, danos à infraestrutura e até a perda de vidas humanas.

Abaixo, estão detalhados três dos casos mais famosos e devastadores da história da computação.

---

## 1. Therac-25 (1985–1987): A Falha Letal em Equipamentos Médicos

O Therac-25 era um acelerador linear de radioterapia de ponta, controlado por software, desenvolvido para tratar pacientes com câncer. Diferente de seus predecessores, que possuíam travas de segurança físicas de hardware, o Therac-25 confiava inteiramente em sua programação para garantir a segurança da operação.

*   **O Bug:** O sistema continha um erro clássico de sincronização conhecido como *race condition* (condição de corrida). Se o operador digitasse os comandos no terminal mais rápido do que o sistema conseguia processar a mudança de estado mecânico, a máquina entrava em um estado inconsistente.
*   **A Consequência Técnica:** O feixe de elétrons era ativado em potência máxima sem posicionar a placa de metal que deveria atenuar e espalhar a radiação de forma segura. 
*   **O Impacto na Sociedade:** Pelo menos seis pacientes receberam overdoses massivas de radiação, chegando a até 100 vezes a dose prescrita. O erro causou queimaduras severas, envenenamento por radiação e resultou em três mortes diretas. O caso mudou profundamente os protocolos globais de teste e certificação de software em equipamentos médicos.

---

## 2. Knight Capital Group (2012): O Pesadelo do Algoritmo de Negociação

A Knight Capital era uma das maiores empresas de negociação de alta frequência (*high-frequency trading*) dos EUA. Em agosto de 2012, a empresa implementou uma atualização de software em seus roteadores para se adequar a um novo formato de negociação na Bolsa de Valores de Nova York.

*   **O Bug:** Durante a implantação, um dos oito servidores da empresa não recebeu o código atualizado. Para agravar o erro de *deploy*, os programadores reutilizaram uma "flag" (sinalizador de código) que, no sistema antigo, servia para ativar um algoritmo de testes morto chamado *Power Peg* — uma função criada anos antes apenas para gerar volume artificial comprando na alta e vendendo na baixa.
*   **A Consequência Técnica:** Quando o novo sistema entrou no ar, ele enviou a "flag" para todos os servidores. O servidor desatualizado interpretou o comando ativando o *Power Peg* diretamente no ambiente de produção real, enviando milhões de ordens sem travas de risco.
*   **O Impacto na Sociedade:** Em apenas 45 minutos, o algoritmo descontrolado realizou mais de 4 milhões de negociações em 154 ações diferentes. O sistema perdeu impressionantes 460 milhões de dólares (cerca de 10 milhões de dólares por minuto). A falha quase levou a gigante financeira à falência instantânea e causou pânico momentâneo na bolsa, transformando-se no maior estudo de caso sobre a importância de testes de *deploy* e DevOps.

---

## 3. Sistema de Defesa Patriot (1991): O Desvio de Relógio Fatal

Durante a Guerra do Golfo, o Exército dos Estados Unidos utilizou o sistema de mísseis antiaéreos Patriot para interceptar mísseis Scud disparados pelo Iraque. No dia 25 de fevereiro de 1991, uma bateria baseada em Dhahran, na Arábia Saudita, falhou gravemente em proteger o espaço aéreo.

*   **O Bug:** O sistema de rastreamento calculava o tempo multiplicando o valor de um relógio interno por um número de 24 bits. Como o sistema contava o tempo em frações e não lidava perfeitamente com a precisão dos decimais no sistema binário, havia um minúsculo erro de arredondamento a cada ciclo. Como a bateria foi deixada ligada ininterruptamente por mais de 100 horas, o erro se acumulou gerando um desvio (*clock drift*) de aproximadamente um terço de segundo.
*   **A Consequência Técnica:** Para um alvo viajando a velocidades supersônicas (cerca de 1.600 metros por segundo), um atraso de um terço de segundo significava que o radar do sistema procurava o míssil inimigo em uma posição mais de 600 metros longe de onde ele realmente estava.
*   **O Impacto na Sociedade:** O míssil iraquiano passou despercebido pelo sistema de interceptação e atingiu um quartel militar americano. O impacto resultou na morte de 28 soldados e deixou quase 100 feridos. O incidente expôs o perigo letal de ignorar limites de precisão matemática em códigos operacionais de longo tempo de atividade.
