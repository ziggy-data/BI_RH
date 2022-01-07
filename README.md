# BI_RH
Nesse projeto estou estudando métricas de RH e novas funções do Power BI como o uso de ferramentas de acessibilidade e menu interativo e análise com storytelling em estudo de cursos.

Neste Projeto eu tive a oportunidade de aprender: 

# Storytelling:
Como comunicar os dados atráves de storytelling com destaque com cores para facilitar o entendimento e uma narrativa concisa. 


![pag1](./dados/img/pag1.png "pagina um")	
![pag2](./dados/img/pag2.png "pagina dois")	
![pag3](./dados/img/pag3.png "pagina tres")	


# Acessibilidade:

Uso da seleção para ajudar usuários que usam apenas o botão "TAB" 

![selecaoRH](./dados/img/selecaoRH.png "Guia de seleção PowerBI")	

# Menu interativo:
Utilizando um menu de filtros com foco em segmentação de dados.

![menuRH](./dados/img/menuRH.png "Menu de filtro com segmentos de dados")	

# Métricas de RH:

* Absenteismo:
    ```
    absenteismo = CALCULATE(
    COUNT(Tb_contratacoes[NomeEmpregado]) * AVERAGE(Tb_contratacoes[Faltas])
    /
    (COUNT(Tb_contratacoes[NomeEmpregado])*20),
    Tb_contratacoes[MotivoSaida] = "Continua empregado"
    )
    ```
    
* metaAbsteteismo:
    ```
    metaAbsenteismo = 0.05 
    ```


* Admissoes:
    ```
    admissoes = COUNTROWS(Tb_contratacoes) 
    ```
    
* Admissoes:
    ```
    desligamentos = CALCULATE(COUNTROWS(Tb_contratacoes),Tb_contratacoes[Status] <> "Ativo")
    ```
    
* funcionariosAtivos:
    ```
    funcionariosAtivos = 
    var AdmissoesAcumulado  = CALCULATE([admissoes],FILTER(all(Tb_contratacoes),[DataContratacao] <= max([DataContratacao])))
    var DesligamentosAcumulado = CALCULATE([desligamentos],FILTER(all(Tb_contratacoes),[DataContratacao] <= max([DataContratacao])))
    return AdmissoesAcumulado - DesligamentosAcumulado 
    ```
* turnoverGeral
    ```
    turnoverGeral = DIVIDE(([admissoes]+[desligamentos])/2 , [funcionariosAtivos])
    ```
    
* metaTurnoverGeral
  ```
  metaTurnoverGeral = 0.1 
  ```

* turnoverDesligamentos
  ```
  turnoverDesligamentos = DIVIDE([desligamentos] , [funcionariosAtivos]) 
  ```

* saldo
  ```
  saldo = [admissoes]-[desligamentos]
  ```

# Modelo relacional

![relacionamentoRH](./dados/img/relacionamentoRH.png "Relacionamento RH")	



# Link dashboard

https://app.powerbi.com/reportEmbed?reportId=eb14195e-1c06-406e-b513-704d4745e8fe&autoAuth=true&ctid=da49a844-e2e3-40af-86a6-c3819d704f49&config=eyJjbHVzdGVyVXJsIjoiaHR0cHM6Ly93YWJpLWJyYXppbC1zb3V0aC1yZWRpcmVjdC5hbmFseXNpcy53aW5kb3dzLm5ldC8ifQ%3D%3D


