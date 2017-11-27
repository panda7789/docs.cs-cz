---
title: Vyberte (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3123d76d5999d9f7201e1415d6bc4313f9767098
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="select-entity-sql"></a>Vyberte (entita SQL)
Určuje prvky vrácených dotazem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Arguments  
 VŠECHNY  
 Určuje, že duplicitní může zobrazit v sadě výsledků dotazu. VŠECHNY je výchozí.  
  
 ODLIŠNÉ  
 Určuje, že můžete pouze jedinečné výsledky se zobrazí v sadě výsledků dotazu.  
  
 HODNOTA  
 Umožňuje zadat, pouze jedinou položku a nepřidá na řádek obálku.  
  
 `topSubclause`  
 Libovolný platný výraz, který označuje číslo, které první výsledků vrácených z dotazu, formuláře `top (``expr``)`.  
  
 Parametr LIMIT [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operátor také umožňuje vybrat prvních n položek v sadě výsledků dotazu.  
  
 `aliasedExpr`  
 Výraz ve tvaru:  
  
 `expr`jako `identifier` &#124;`expr`  
  
 `expr`  
 Literál nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule SELECT vyhodnotí po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), a [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) byly vyhodnoceny klauzule. Klauzule SELECT může odkazovat pouze na položky aktuálně oboru (z klauzule FROM nebo z vnějšího oborů). Pokud byla zadána klauzule GROUP BY, klauzule SELECT je povoleno pouze tak, aby odkazovaly aliasy pro klíče GROUP BY. Odkazy na položky klauzule FROM je povolená jenom v agregačních funkcích.  
  
 Seznam následující klíčového slova vyberte jeden nebo více výrazů dotazu se označuje jako seznamu příkazu select nebo oficiálně jako projekce. Většina Obecná forma projekce je výraz jeden dotaz. Pokud vyberete členem `member1` z kolekce `collection1`, vytvoří novou kolekci všech `member1` hodnoty pro každý objekt v `collection1`, jak je popsáno v následujícím příkladu.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Například pokud `customers` je kolekce typu `Customer` má vlastnost `Name` , je typu `string`, vyberete `Name` z `customers` předá kolekce řetězce, jak je znázorněno v následujícím příkladu .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 Je také možné použití syntaxe spojení (FULL, vnitřní, vlevo, vnější, ON a vpravo). Dále je potřeba pro vnitřní spojení a je nChcete-li povolena křížové spojení.  
  
## <a name="row-and-value-select-clauses"></a>Řádek a hodnota klauzule FROM  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]podporuje dvě varianty klauzuli SELECT. První variant, vyberte řádek, je identifikována vyberte – klíčové slovo a umožňuje určit jednu nebo více hodnot, které by měl použít k projekci se. Protože implicitně přidání řádek obálku kolem hodnot vrácených výsledkem výrazu dotazu je vždy multimnožina řádků.  
  
 Každý výraz dotazu v vyberte řádek zadejte alias. Pokud není zadaný žádný alias,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí generování alias pomocí pravidel pro vytvoření aliasu.  
  
 Další varianta klauzuli SELECT, vyberte hodnotu, je identifikován – klíčové slovo SELECT VALUE. Umožňuje zadat, pouze jednu hodnotu a nepřidává žádné další řádek obálku.  
  
 Vyberte řádek je vždy vyjádřit kombinací z hlediska hodnotu vyberte, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Všechny a odlišné modifikátory  
 Obě variant vyberte v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] povolit specifikace všech nebo odlišné modifikátor. Pokud je zadán odlišné modifikátor, duplicitní položky se odstraní z kolekce vyprodukované výrazu dotazu (do a včetně klauzule SELECT). Pokud se všechny modifikátor zadaný, ne duplicitní odstranění probíhá; VŠECHNY je výchozí.  
  
## <a name="differences-from-transact-sql"></a>Rozdíl oproti Transact-SQL  
 Na rozdíl od jazyka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje použití * argument v klauzuli SELECT.  Místo toho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazy do projektu se celé záznamy odkazem aliasy kolekce z klauzule FROM, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Předchozí [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazu dotazu je vyjádřena v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor SELECT zadat prvky, které mají být vrácených dotazem. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Viz také  
 [Výrazy dotazů](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [HORNÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
