# Restructuring_VectorPostalAddress_DataFrame
Reestruturação de uma tabela de dados vetoriais de endereço, em um arquivo 'csv' de consulta de CEP e endereço.

05/01/2021

Esse exercício consistiu em transformar uma tabela de uma base vetorial de endereços em uma outra tabela simplificada para consulta de CEP e endereço contendo a maior e menor numeração de cada logradouro por CEP.

A tabela original, por ser vetorial, continha muitos segmentos de linha para cada logradouro. Outra característica é que ela continha duas colunas para CEP, do lado esquerdo e direito da rua. O mesmo para a numeração do logradouro: numeração inicial e final de cada segmento de linha para os dois lados da rua - num total de quatro colunas de numeração.

O objetivo era agrupar ('merge' para vetores e 'groupby' no Pandas) toda a planilha por CEP e Logradouro e criar uma coluna com o menor e outra com o maior número dos terrenos por CEP e Logradouro.

O primeiro passo antes do script foi gerar um arquivo csv a partir da tabela do vetor de arruamento.

Para isso, depois de selecionar os campos a serem usados e renomeá-los, as duas colunas referentes ao CEP (da direita e da esquerda da rua) foram "empilhadas", através de concatenação, transformando-as em uma única coluna. O mesmo procedimento foi feito para a numeração de rua do lado direito e esquerdo de cada segmento de rua.

Foi necessário forçar a numeração de rua a ter o formato float, apesar de que a numeração é sempre de números inteiros.

O tipo float permite que existam valores nulos (NaN) onde não havia essa informação na tabela original. Se os números fossem transformados logo para integer, os campos nulos seriam transformados em 0, inviabilizando selecionar o menor número da rua, uma vez que numeração de rua igual a zero não existe, e ainda aceitando a possibilidade de que um CEP e Logradouro podem não ter a numeração preenchida na base original.

Os números foram convertidos para integer apenas no final do script.

De saída o DataFrame final foi exportado para csv.
