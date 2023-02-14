# risadinhas-onipresentes
Acessar o datalake da Base dos Dados no Power BI. 

O objetivo é conectar o serviço de banco de dados em nuvem do Google, Bigquery, 
onde o conjunto de dados da Base dos Dados estão armazenados dentro de um datalke público - 
chamado basedosdados no Power BI.

Os dados coletados foram do siconfi, e referem-se aos gastos públicos municipais em saúde, educação e segurança pública 
do estado do Rio Grande do Sul, a partir de 2010. 

Comandos em SQL:


SELECT  
  ano, 
  SUBSTR(id_municipio, 1, 6) AS id_municipio, 
  estagio_bd, 
  conta_bd, 
  valor
FROM `basedosdados.br_me_siconfi.municipio_despesas_funcao` AS gastos_publicos
WHERE ano > 2009
AND id_municipio LIKE '43%'
AND estagio_bd = 'Despesas Empenhadas'
AND conta_bd in ('Saúde', 'Educação', 'Segurança Pública')
ORDER BY ANO ASC
