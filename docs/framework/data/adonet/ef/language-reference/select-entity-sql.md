---
title: VYBRAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 4142dca604c0f6dd521f45a8cadd26b9574000f0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319368"
---
# <a name="select-entity-sql"></a>VYBRAT (Entity SQL)
Určuje prvky vrácené dotazem.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Arguments  
 VŠEM  
 Určuje, že se duplikáty můžou objevit v sadě výsledků dotazu. Výchozí hodnota je ALL.  
  
 ZNAK  
 Určuje, že v sadě výsledků se můžou vyskytovat jenom jedinečné výsledky.  
  
 OSA  
 Povoluje zadání pouze jedné položky a nepřidá se na obálku řádku.  
  
 `topSubclause`  
 Libovolný platný výraz, který určuje počet prvních výsledků, které se mají vrátit z dotazu, z formuláře `top(expr)`.  
  
 Parametr LIMIT operátoru [ORDER by](order-by-entity-sql.md) také umožňuje vybrat prvních n položek v sadě výsledků dotazu.  
  
 `aliasedExpr`  
 Výraz formuláře:  
  
 `expr` jako `identifier` &#124; `expr`  
  
 `expr`  
 Literál nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule SELECT je vyhodnocena po vyhodnocení klauzulí [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)a [having](having-entity-sql.md) . Klauzule SELECT může odkazovat pouze na položky aktuálně nacházející se v oboru (z klauzule FROM nebo z vnějších oborů). Pokud je zadána klauzule GROUP BY, klauzule SELECT je povolena pouze pro odkazy na aliasy pro skupinu podle klíčů. Odkazování na položky klauzule FROM je povoleno pouze v agregačních funkcích.  
  
 Seznam jednoho nebo více výrazů dotazů za klíčovým slovem SELECT je známý jako seznam pro výběr, nebo je ve formě projekce složitější. Nejobecnější forma projekce je jeden výraz dotazu. Pokud vyberete člena `member1` z kolekce `collection1`, vytvoří se nová kolekce všech hodnot `member1` pro každý objekt v `collection1`, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 Například pokud je `customers` kolekce typu `Customer`, který má vlastnost `Name` typu `string`, výběr `Name` z `customers` zaznamená kolekci řetězců, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 Také je možné použít syntaxi spojení (FULL, vnitřní, levý, vnější, ZAPNUTý a pravý). ON se vyžaduje pro vnitřní spojení a u vzájemných spojení je k v-nChcete-li povolený.  
  
## <a name="row-and-value-select-clauses"></a>Klauzule SELECT pro řádek a hodnotu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dvě varianty klauzule SELECT. První varianta, výběr řádku, je identifikována klíčovým slovem SELECT a lze ji použít k zadání jedné nebo více hodnot, které by měly být vyhodnoceny jako neočekávané. Vzhledem k tomu, že se obálka řádku implicitně přidala kolem vrácených hodnot, je výsledek výrazu dotazu vždycky multiset řádků.  
  
 Každý výraz dotazu v řádku SELECT musí určovat alias. Pokud není zadán žádný alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí vygenerovat alias pomocí pravidel generování aliasu.  
  
 Druhá varianta klauzule SELECT, hodnota SELECT, je identifikována klíčovým slovem SELECT VALUE. Umožňuje zadat pouze jednu hodnotu a nepřidá obálku řádku.  
  
 Výběr řádku je vždy vyhodnotit ve smyslu hodnoty SELECT, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Modifikátory All a DISTINCT  
 Obě varianty výběru v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňují specifikaci modifikátoru ALL nebo DISTINCT. Je-li zadán modifikátor DISTINCT, jsou duplicity odstraněny z kolekce vytvořené výrazem dotazu (až do klauzule SELECT). Pokud je zadán modifikátor ALL, není provedeno žádné duplicitní eliminace; Výchozí hodnota je ALL.  
  
## <a name="differences-from-transact-sql"></a>Rozdíly v jazyce Transact-SQL  
 Na rozdíl od jazyka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje použití argumentu * v klauzuli SELECT.  Místo toho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazům vydávat celé záznamy pomocí odkazů na aliasy kolekce z klauzule FROM, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 Předchozí výraz dotazu Transact-SQL je vyjádřen v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem.  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor SELECT k určení prvků, které mají být vráceny dotazem. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Viz také:

- [Výrazy dotazu](query-expressions-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [TOP](top-entity-sql.md)
