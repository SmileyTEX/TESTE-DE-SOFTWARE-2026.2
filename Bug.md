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

## 2. Foguete Ariane 5 - Voo 501 (1996): O Erro de Conversão de 370 Milhões de Dólares

O projeto do foguete europeu Ariane 5 levou uma década para ser desenvolvido, com um custo na casa dos bilhões para a Agência Espacial Europeia (ESA). Seu aguardado voo inaugural ocorreu em 4 de junho de 1996, carregando um conjunto de satélites científicos.

*   **O Bug:** Ocorreu um *integer overflow* (estouro numérico) no código do Sistema de Referência Inercial. O software (que havia sido reaproveitado do foguete anterior, o Ariane 4) tentou converter um número de ponto flutuante de 64 bits em um número inteiro com sinal de 16 bits. O valor da aceleração do Ariane 5 era muito maior que a do Ariane 4 e excedeu o limite máximo que os 16 bits podiam armazenar.
*   **A Consequência Técnica:** O computador de navegação travou e repassou dados de diagnóstico de erro como se fossem dados reais de voo. O sistema principal interpretou isso como um desvio extremo de rota e ordenou uma correção abrupta nos motores.
*   **O Impacto na Sociedade:** Apenas 37 segundos após o lançamento, as intensas forças aerodinâmicas despedaçaram o foguete, acionando seu mecanismo de autodestruição. O prejuízo imediato foi de aproximadamente 370 milhões de dólares entre a carga e o lançador, tornando-se um dos bugs mais notórios e caros da engenharia de software.

---

## 3. Sistema de Defesa Patriot (1991): O Desvio de Relógio Fatal

Durante a Guerra do Golfo, o Exército dos Estados Unidos utilizou o sistema de mísseis antiaéreos Patriot para interceptar mísseis Scud disparados pelo Iraque. No dia 25 de fevereiro de 1991, uma bateria baseada em Dhahran, na Arábia Saudita, falhou gravemente em proteger o espaço aéreo.

*   **O Bug:** O sistema de rastreamento calculava o tempo multiplicando o valor de um relógio interno por um número de 24 bits. Como o sistema contava o tempo em frações e não lidava perfeitamente com a precisão dos decimais no sistema binário, havia um minúsculo erro de arredondamento a cada ciclo. Como a bateria foi deixada ligada ininterruptamente por mais de 100 horas, o erro se acumulou gerando um desvio (*clock drift*) de aproximadamente um terço de segundo.
*   **A Consequência Técnica:** Para um alvo viajando a velocidades supersônicas (cerca de 1.600 metros por segundo), um atraso de um terço de segundo significava que o radar do sistema procurava o míssil inimigo em uma posição mais de 600 metros longe de onde ele realmente estava.
*   **O Impacto na Sociedade:** O míssil iraquiano passou despercebido pelo sistema de interceptação e atingiu um quartel militar americano. O impacto resultou na morte de 28 soldados e deixou quase 100 feridos. O incidente expôs o perigo letal de ignorar limites de precisão matemática em códigos operacionais de longo tempo de atividade.
