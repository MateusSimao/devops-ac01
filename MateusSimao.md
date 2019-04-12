
select Modelo.descricao,Fabricante.Nome ,Veiculo.descricao, ano, sum (isnull(qtd, 0)) as 'Veiculo BMW F800 GS'
from Veiculo join

	   Modelo on Modelo.idModelo = Veiculo.idModelo join
	   VendasAnuais on Veiculo.idVeiculo = VendasAnuais.idVeiculo join
	   Ano on VendasAnuais.idAnodaVenda = Ano.idAno join
	   Fabricante on Veiculo.idFabricante = Fabricante.idFabricante

	   where Veiculo.descricao = 'F800'
	   and Modelo.descricao = 'GS'
	   and Fabricante.Nome = 'BMW'
	   and (valor > 6521.97 or valor < 5967.43)
	   group by Ano.ano, Veiculo.descricao, Modelo.descricao, Fabricante.Nome



-- 2
SELECT 
    TOP 1
    v.idVeiculo,
    AVG(qtd) AS 'Média de Vendas'
FROM VendasAnuais v
GROUP BY v.idMesdaVenda, v.idVeiculo
ORDER BY AVG(qtd) DESC

-- 3

SELECT 
    ve.Descricao AS 'Veiculo',
    f.nome AS 'Fabricante',
    m.Descricao AS 'Modelo',
    a.ano AS 'Ano',
    me.mes AS 'Mes',
    v.qtd
FROM Veiculo ve
INNER JOIN VendasAnuais v ON v.idVeiculo = ve.idVeiculo
INNER JOIN Ano a ON v.idAnodaVenda = a.idAno
INNER JOIN Mes me ON v.idMesdaVenda = me.idMes
INNER JOIN Modelo m ON ve.idModelo = m.idModelo
INNER JOIN Fabricante f ON ve.idFabricante = f.idFabricante
WHERE v.idVeiculo = 56 AND (me.mes IN (1, 3) OR me.mes IN (10, 12));
