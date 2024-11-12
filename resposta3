import xml.etree.ElementTree as ET

# Função para ler o arquivo XML e retornar os dados de faturamento
def ler_faturamento_xml(arquivo_xml):
    # Carrega o arquivo XML
    tree = ET.parse(arquivo_xml)
    root = tree.getroot()
    
    # Lista para armazenar os valores de faturamento
    faturamentos = []
    
    # Itera sobre cada linha no XML e pega o valor do faturamento
    for row in root.findall('row'):
        valor = float(row.find('valor').text)  # Obtém o valor de faturamento
        faturamentos.append(valor)
    
    return faturamentos

# Função para calcular o menor valor de faturamento
def calcular_menor_faturamento(faturamentos):
    # Ignora os dias com faturamento zero
    faturamentos_filtrados = [f for f in faturamentos if f > 0]
    return min(faturamentos_filtrados) if faturamentos_filtrados else 0

# Função para calcular o maior valor de faturamento
def calcular_maior_faturamento(faturamentos):
    # Ignora os dias com faturamento zero
    faturamentos_filtrados = [f for f in faturamentos if f > 0]
    return max(faturamentos_filtrados) if faturamentos_filtrados else 0

# Função para calcular a média mensal
def calcular_media_mensal(faturamentos):
    # Ignora os dias com faturamento zero
    faturamentos_filtrados = [f for f in faturamentos if f > 0]
    return sum(faturamentos_filtrados) / len(faturamentos_filtrados) if faturamentos_filtrados else 0

# Função para contar o número de dias com faturamento superior à média
def contar_dias_superiores_media(faturamentos, media):
    return len([f for f in faturamentos if f > media])

# Função principal
def analisar_faturamento(arquivo_xml):
    # Lê os dados de faturamento do XML
    faturamentos = ler_faturamento_xml(arquivo_xml)
    
    # Calcula o menor valor de faturamento
    menor_faturamento = calcular_menor_faturamento(faturamentos)
    
    # Calcula o maior valor de faturamento
    maior_faturamento = calcular_maior_faturamento(faturamentos)
    
    # Calcula a média mensal
    media_mensal = calcular_media_mensal(faturamentos)
    
    # Conta os dias com faturamento superior à média
    dias_superiores_media = contar_dias_superiores_media(faturamentos, media_mensal)
    
    # Exibe os resultados
    print(f"Menor valor de faturamento: {menor_faturamento:.2f}")
    print(f"Maior valor de faturamento: {maior_faturamento:.2f}")
    print(f"Número de dias com faturamento superior à média: {dias_superiores_media}")

# Caminho para o arquivo XML
arquivo_xml = 'dados.xml'

# Chama a função para analisar o faturamento
analisar_faturamento(arquivo_xml)
