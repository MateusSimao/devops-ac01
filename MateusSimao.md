
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
WHERE v.idVeiculo = 14 AND (me.mes IN (1, 3) OR me.mes IN (10, 12));
