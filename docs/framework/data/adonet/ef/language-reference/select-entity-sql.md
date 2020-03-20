---
title: SELECT (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149906"
---
# <a name="select-entity-sql"></a>SELECT (Entita SQL)
Určuje prvky vrácené dotazem.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Argumenty  
 VŠE  
 Určuje, že se ve výsledkové sadě mohou objevit duplikáty. ALL je výchozí.  
  
 DISTINCT  
 Určuje, že se ve výsledkové sadě mohou objevit pouze jedinečné výsledky.  
  
 HODNOTA  
 Umožňuje zadat pouze jednu položku a nepřidá obálku řádku.  
  
 `topSubclause`  
 Libovolný platný výraz, který označuje počet prvních výsledků, které `top(expr)`se mají vrátit z dotazu formuláře .  
  
 Parametr LIMIT operátoru [OBJET](order-by-entity-sql.md) PODLE také umožňuje vybrat první n položek v sadě výsledků.  
  
 `aliasedExpr`  
 Výraz formuláře:  
  
 `expr`jako `identifier` &#124;`expr`  
  
 `expr`  
 Literál nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule SELECT je vyhodnocena po vyhodnocených klauzulích [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)a [HAVING.](having-entity-sql.md) Select klauzule může odkazovat pouze na položky, které jsou aktuálně v oboru (z klauzule FROM nebo z vnějších oborů). Pokud group by klauzule byla zadána, SELECT klauzule je povoleno pouze odkazovat na aliasy pro group by klíče. Odkazování na položky klauzule FROM je povoleno pouze v souhrnných funkcích.  
  
 Seznam jednoho nebo více výrazů dotazu za klíčovým slovem SELECT se označuje jako seznam výběru nebo formálněji jako projekce. Nejobecnější formou projekce je výraz jednoho dotazu. Pokud vyberete `member1` člena z `collection1`kolekce , vytvoříte novou `member1` kolekci všech `collection1`hodnot pro každý objekt v , jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 Například pokud `customers` je kolekce `Customer` typu, který `Name` má vlastnost, která je typu `string`, výběr `Name` z `customers` přinese kolekci řetězců, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 Je také možné použít syntaxi JOIN (ÚPLNÁ, VNITŘNÍ, LEVÁ, VNĚJŠÍ, ZAPNUTÁ A PRAVÁ). ON je vyžadován pro vnitřní spojení a je nto povoleno pro křížové spojení.  
  
## <a name="row-and-value-select-clauses"></a>Klauzule pro výběr řádků a hodnot  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje dvě varianty klauzule SELECT. První varianta, výběr řádku, je identifikována klíčovým slovem SELECT a lze ji použít k určení jedné nebo více hodnot, které by měly být promítnuty. Vzhledem k tomu, že obálka řádku je implicitně přidána kolem vrácených hodnot, je výsledkem výrazu dotazu vždy vícenásobná sada řádků.  
  
 Každý výraz dotazu v řádku select musí určit alias. Pokud není zadán[!INCLUDE[esql](../../../../../../includes/esql-md.md)] žádný alias, pokusí se vygenerovat alias pomocí pravidel generování aliasu.  
  
 Druhá varianta klauzule SELECT, vyberte hodnotu, je identifikována klíčovým slovem SELECT VALUE. Umožňuje zadat pouze jednu hodnotu a nepřidá obálku řádku.  
  
 Výběr řádku je vždy vyjádřitelný z hlediska FUNKCE VALUE SELECT, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a>Všechny a odlišné modifikátory  
 Obě varianty SELECT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in umožňují specifikaci modifikátoru ALL nebo DISTINCT. Pokud je zadán modifikátor DISTINCT, duplikáty jsou odstraněny z kolekce vytvořené výrazem dotazu (až do klauzule SELECT včetně). Pokud je zadán modifikátor ALL, neprovede se žádná duplicitní eliminace; ALL je výchozí.  
  
## <a name="differences-from-transact-sql"></a>Rozdíly od Transact-SQL  
 Na rozdíl od [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL nepodporuje použití * argument v select klauzule.  Místo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] toho umožňuje dotazy promítnout celé záznamy odkazem na aliasy kolekce z from klauzule FROM, jak je znázorněno v následujícím příkladu.  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 Předchozí výraz dotazu Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je vyjádřen následujícím způsobem.  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz ENTITY SQL používá operátor SELECT k určení prvků, které mají být vráceny dotazem. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>Viz také

- [Výrazy dotazu](query-expressions-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Top](top-entity-sql.md)
