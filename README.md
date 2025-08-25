# AWS-Redu-oDeCustos
# RELATÓRIO DE IMPLEMENTAÇÃO DE SERVIÇOS AWS

## # Introdução

Este relatório apresenta o processo de implementação de ferramentas na empresa Novo, realizado por Arthur. O objetivo do projeto foi elencar 3 serviços AWS, com a finalidade de realizar diminuição de custos imediatos.

## # Descrição do Projeto

O projeto de implementação de ferramentas foi dividido em 3 etapas, cada uma com seus objetivos específicos. A seguir, serão descritas as etapas do projeto:

### Etapa 1:

- [Nome da ferramenta] → **Amazon S3**
- [Foco da ferramenta] → **Armazenamento de dados de farmácia**
- [Descrição de caso de uso] → **Armazenar dados de vendas diárias para análise de custo**

### Etapa 2:

- [Nome da ferramenta] → **AWS Lambda + Amazon Athena**
- [Foco da ferramenta] → **Processamento e análise de dados**
- [Descrição de caso de uso] → **Analisar custos de estoque excedente para redução**

### Etapa 3:

- [Nome da ferramenta] → **Amazon CloudWatch + AWS Cost Explorer**
- [Foco da ferramenta] → **Monitoramento e otimização de custos**
- [Descrição de caso de uso] → **Gerar alertas e relatórios para reduzir gastos**

## # (Opcional) Resultados

[Descreva aqui os resultados estimados, ex.: "Redução de 15% nos custos ao implementar Lambda e otimizar armazenamento no S3."]

# Codigo Lambda-Python

import boto3
import json

s3_client = boto3.client('s3')

def lambda_handler(event, context):
bucket = event['Records'][0]['s3']['bucket']['name']
file = event['Records'][0]['s3']['object']['key']
s3_client.download_file(bucket, file, '/tmp/data.csv') # Adicione lógica para processar o CSV (ex.: pandas ou csv module)
return {
'statusCode': 200,
'body': json.dumps('Processado com sucesso')
}
