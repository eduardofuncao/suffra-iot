![image](https://github.com/user-attachments/assets/80105000-b21e-4306-9881-bba26e4d187e)

# 🌐 Suffra Backend Server  
API REST desenvolvida com Java Springboot para o aplicativo Suffra, desenvolvido como solução de gerenciamento de campanhas de conscientização relacionadas com energia sustentável.  
Link GitHub: https://github.com/eduardofuncao/suffra-iot

## 👥 Equipe  
- Artur Lopes Fiorindo         53481  
- Eduardo Felipe Nunes Função  553362  
- Jhoe Yoshio Kochi Hashimoto  553831  

## 🎥 Vídeos
https://youtu.be/v18d1QvW-Oo

## 📖 Contextualização  
**Suffra** é um projeto que implementa uma competição gamificada para introdução de campanhas de conscientização para a população.  

### 📊 Compreendendo as entidades do sistema  
De forma genérica, para cada **campanha**, os **usuários** contribuirão por meio de **votos** para alguma **região**. Ao final do período de campanha, a região com maior quantidade de votos será determinada a vencedora, sendo contemplada com algum benefício.  

> REGIÃO  -> Torres de um condomínio  
> VOTO    -> Entradas de gastos energéticos por Torre  
> USUÁRIO -> Morador do condomínio  

### ⚡ Como será utilizado nessa Entrega
Especificamente, a proposta apresentada será uma campanha de conscientização sobre redução no consumo energético de torres de um condomínio residencial.  

Ao final do período da campanha, a torre com menores gastos energéticos será a vencedora, garantindo aos seus moradores um desconto na conta de condomínio.  

### 🚀 Extensões futuras  
Como o sistema foi idealizado para ser utilizado em outras categorias que não o consumo energético, seria possível adaptá-lo para campanhas como:  
- 💧 Redução do consumo de água  
- ♻️ Incentivo à reciclagem de lixo  
- 🤝 Doações para causas sociais relacionadas à energia sustentável  

---

## **Modelagem com Machine Learning**
Para auxiliar as expansões futuras do projeto, foi desenvolvido um estudo de Machine Learning para analisar um série de dados que relacionam o clima de uma determinada região ao consumo energético residencial.
Mais especificamente, trata-se de uma base de dados que possui duas tabelas principais. Uma do consumo energético diário de diversas resisdências de Londres dentro de um período de tempo. E outro com as condições metereológicas da cidade por dia (temperatura, vento, umidade, etc.).
O dataset pode ser encontrado [neste link do kaggle](https://www.kaggle.com/datasets/jeanmidev/smart-meters-in-london/data?select=daily_dataset.csv).
A ideia central da análise é que seja criado um modelo que seja capaz de predizer o consumo energético de uma residência ao longo do dia, tendo em base somente as condições de clima da região e os dados históricos de consumo energético.

## Metodologia
Para preparação do dataset, dados nulos e duplicados foram removidos, os dados foram normalizadose foi verificado a possibilidade de remoção de outliers e duplas de dados com alta correlação. Também será discutio sobre a utilização de técnicas de redução de dimensionalidade como o PCA.
Antes dos testes, os dados foram particionados em uma amostra aleatória de 20% do dataset original, o que agilizou todo o processo de treinamento.

Para o desenvolvimento desta análise, serão feitos treinamentos distintos, com 4 modelos de **Regressão** diferentes:
1. Árvore de Decisão
2. Random Forest
3. Artificial Neural Network
4. SGD

Após o treinamento e predição, os modelos serão avaliados de acorodo com os critérios de rapidez de execução, erro médio absoluto e erro médio quadrático, e R².

## Resultados 

### Dados Utilizados após união de tabelas e tratamentos
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>LCLid</th>
      <th>energy_median</th>
      <th>energy_mean</th>
      <th>energy_max</th>
      <th>energy_count</th>
      <th>energy_std</th>
      <th>energy_sum</th>
      <th>energy_min</th>
      <th>date</th>
      <th>temperatureMax</th>
      <th>...</th>
      <th>sunriseTime</th>
      <th>temperatureHighTime</th>
      <th>uvIndexTime</th>
      <th>summary</th>
      <th>temperatureLowTime</th>
      <th>apparentTemperatureMin</th>
      <th>apparentTemperatureMaxTime</th>
      <th>apparentTemperatureLowTime</th>
      <th>moonPhase</th>
      <th>is_holiday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MAC000131</td>
      <td>0.4850</td>
      <td>0.432045</td>
      <td>0.868</td>
      <td>22</td>
      <td>0.239146</td>
      <td>9.505</td>
      <td>0.072</td>
      <td>2011-12-15</td>
      <td>7.97</td>
      <td>...</td>
      <td>2011-12-15 08:00:46</td>
      <td>2011-12-15 14:00:00</td>
      <td>2011-12-15 11:00:00</td>
      <td>Partly cloudy throughout the day and breezy in...</td>
      <td>2011-12-16 08:00:00</td>
      <td>1.07</td>
      <td>2011-12-15 21:00:00</td>
      <td>2011-12-16 08:00:00</td>
      <td>0.66</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>MAC000131</td>
      <td>0.1415</td>
      <td>0.296167</td>
      <td>1.116</td>
      <td>48</td>
      <td>0.281471</td>
      <td>14.216</td>
      <td>0.031</td>
      <td>2011-12-16</td>
      <td>4.68</td>
      <td>...</td>
      <td>2011-12-16 08:01:35</td>
      <td>2011-12-16 15:00:00</td>
      <td>2011-12-16 11:00:00</td>
      <td>Mostly cloudy throughout the day.</td>
      <td>2011-12-17 08:00:00</td>
      <td>-2.65</td>
      <td>2011-12-16 00:00:00</td>
      <td>2011-12-17 08:00:00</td>
      <td>0.70</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>MAC000131</td>
      <td>0.1015</td>
      <td>0.189812</td>
      <td>0.685</td>
      <td>48</td>
      <td>0.188405</td>
      <td>9.111</td>
      <td>0.064</td>
      <td>2011-12-17</td>
      <td>5.35</td>
      <td>...</td>
      <td>2011-12-17 08:02:21</td>
      <td>2011-12-17 14:00:00</td>
      <td>2011-12-17 11:00:00</td>
      <td>Partly cloudy throughout the day.</td>
      <td>2011-12-18 07:00:00</td>
      <td>-3.56</td>
      <td>2011-12-17 15:00:00</td>
      <td>2011-12-18 06:00:00</td>
      <td>0.73</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>MAC000131</td>
      <td>0.1140</td>
      <td>0.218979</td>
      <td>0.676</td>
      <td>48</td>
      <td>0.202919</td>
      <td>10.511</td>
      <td>0.065</td>
      <td>2011-12-18</td>
      <td>5.49</td>
      <td>...</td>
      <td>2011-12-18 08:03:04</td>
      <td>2011-12-18 14:00:00</td>
      <td>2011-12-18 12:00:00</td>
      <td>Partly cloudy until evening.</td>
      <td>2011-12-19 01:00:00</td>
      <td>-4.12</td>
      <td>2011-12-18 14:00:00</td>
      <td>2011-12-19 02:00:00</td>
      <td>0.77</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>MAC000131</td>
      <td>0.1910</td>
      <td>0.325979</td>
      <td>0.788</td>
      <td>48</td>
      <td>0.259205</td>
      <td>15.647</td>
      <td>0.066</td>
      <td>2011-12-19</td>
      <td>6.64</td>
      <td>...</td>
      <td>2011-12-19 08:03:43</td>
      <td>2011-12-19 19:00:00</td>
      <td>2011-12-19 11:00:00</td>
      <td>Partly cloudy throughout the day.</td>
      <td>2011-12-20 04:00:00</td>
      <td>-3.67</td>
      <td>2011-12-19 19:00:00</td>
      <td>2011-12-20 08:00:00</td>
      <td>0.81</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 41 columns</p>
</div>

### Target
energy_sum -> será utilizada a soma do consumo energético ao longo do dia como target de todos os modelos de ML

### Árvore de Decisão com PCA
![image](https://github.com/user-attachments/assets/00629150-9720-42b4-9df9-2cb4c2a5736b)
Mean Absolute Error (MAE): 1.0871239382239475
Mean Squared Error (MSE): 3.4858818351886116
R-squared (R²): 0.9709308172542794

### Árvore de Decisão sem PCA
![image](https://github.com/user-attachments/assets/c23db540-0816-4a3e-a1d5-a5937ad00890)
Mean Absolute Error (MAE): 0.002058332798034988
Mean Squared Error (MSE): 0.013228724004742043
R-squared (R²): 0.9998896840989546

### Random Forest
![image](https://github.com/user-attachments/assets/7b3f2141-76ff-484a-a2e0-163b8b1672a7)
Mean Absolute Error (MAE): 0.6694849608449615
Mean Squared Error (MSE): 1.4597164266726608
R-squared (R²): 0.9879312868774259

### ANN
![image](https://github.com/user-attachments/assets/a3c7c205-7506-446e-948e-c26381eb7b3c)
Mean Absolute Error (MAE): 0.617035284845665
Mean Squared Error (MSE): 1.2656694277988503
R-squared (R²): 0.9895356379136355

### SGD
![image](https://github.com/user-attachments/assets/4c5efc44-8a16-49fb-9a7e-7b7b343831b9)
Mean Absolute Error (MAE): 0.6705781276887761
Mean Squared Error (MSE): 1.633249221525243
R-squared (R²): 0.9864965441560549

## Conclusão
Observando a base de dados analisada, é possível observar que os dados de temperatura e outras condições climáticas geralmente seguem uma distribuição normal, sem a presença de outliers extremos. No caso dos dados de energia, não possuímos informações tão bem comportadas: existem muitos dados zerados devido a possíveis dias sem energia, e muitos dados com picos energéticos altos em relação à maioria dos valores, mas que não podem ser categorizados como outlier para esta pesquisa.

A partir dos resultados obtidos, podemos tirar uma série de informações a respeito do nosso projeto e de nossa modelagem.
No geral, todos os modelos foram capazes de predizer relativamente bem o consumo energético residencial a partir de dados climatológicos, sendo que todos os R² ficaram acima de 0.9, indicando uma boa qualidade de predição nos modelos.
No entanto, dependendo do modelo utilizado, o tempo de execução e o tamanho dos erros quadráticos podem ser pontos de atenção

Em relação ao tempo de execução, destaca-se negativamente o Random Forest, que, apesar de um baixo erro médio, demorou cerca de 5 minutos para execução. em uma máquina de 16GB de RAM e processador de 8 cores. De forma diferente, o modelo SGD foi o mais tempo-eficiente, tendo um resultado comparável ao modelo de Rede Neural, mas podendo ser executado num tempo muito mais reduzido.

Em suma, para o seguimento do projeto, será utilizado o algoritmo SGD, que funciona muito bem para datasets grandes (mais de 1M de entradas)
