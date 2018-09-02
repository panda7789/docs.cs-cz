---
title: Vyberte (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 93eea5d539e943c57ed7c6236caa854486ac238e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402647"
---
# <a name="select-entity-sql"></a>Vyberte (Entity SQL)
Určuje prvků vrácených dotazem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Arguments  
 VŠECHNY  
 Určuje, že duplicitní položky se zobrazí v sadě výsledků. VŠE je výchozí hodnota.  
  
 DISTINCT  
 Určuje, že pouze jedinečné výsledky se zobrazí v sadě výsledků.  
  
 HODNOTA  
 Umožňuje zadat, pouze jednu položku a nedojde k přidání na obálku řádek.  
  
 `topSubclause`  
 Libovolný platný výraz, který označuje počet prvních výsledků vrácených z dotazu ve formuláři `top(expr)`.  
  
 Parametr LIMIT [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operátor také vám umožní vybrat prvních n položek v sadě výsledků.  
  
 `aliasedExpr`  
 Výraz ve tvaru:  
  
 `expr` jako `identifier`&#124; `expr`  
  
 `expr`  
 Literál nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule SELECT je vyhodnocen po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [Group](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), a [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) vyhodnocení klauzule. Klauzule SELECT může odkazovat pouze na položky aktuálně oboru (z klauzule FROM nebo z vnějšího obory). Pokud je zadaná klauzule GROUP BY, klauzule SELECT je povolena pouze tak, aby odkazovaly aliasy pro klíče GROUP BY. Odkazy na položky klauzule FROM je povolená jenom v agregačních funkcích.  
  
 Seznam jedné nebo více výrazů dotazu následující vyberte klíčové slovo se označuje jako seznamu příkazu select nebo formálně jako projekce. Nejobecnější projekce má výraz jeden dotaz. Pokud vyberete člen `member1` z kolekce `collection1`, vytvoří novou kolekci všech `member1` hodnoty pro každý objekt v `collection1`, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Například pokud `customers` je kolekce typu `Customer` , který má vlastnost `Name` , který je typu `string`, kde vyberou `Name` z `customers` předá kolekce řetězců, jak je znázorněno v následujícím příkladu .  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 Je také možné použít syntaxi příkazu JOIN (FULL, vnitřní, vlevo, vnější, ON a vpravo). Dále je třeba vnitřní spojení a je nChcete-li povolen křížové spojení.  
  
## <a name="row-and-value-select-clauses"></a>Řádek a hodnota klauzule FROM  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje dvě varianty klauzule SELECT. První varianta, vyberte řádek, je identifikován vyberte – klíčové slovo a je možné zadat jednu nebo více hodnot, které by měl použít k projekci navýšení kapacity. Protože obálka řádek je implicitně přidat kolem hodnoty vrácené, výsledek výrazu dotazu je vždy použita třída multiset řádků.  
  
 Každý výraz dotazu, vyberte řádek zadejte alias. Pokud není zadán žádný alias,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias pomocí pravidel pro vytvoření aliasu.  
  
 Varianta klauzuli SELECT, vyberte hodnotu, je identifikován – klíčové slovo SELECT VALUE. Umožňuje pouze jednu hodnotu, chcete-li zadán a nedojde k přidání řádku obálku.  
  
 Vyberte řádek je vždy anyAttribute z hlediska hodnota vyberte, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Všechny a odlišné modifikátory  
 Obě varianty, vyberte v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] povolit specifikaci všechny nebo odlišné modifikátor. Pokud je zadán odlišné modifikátor, duplicitní položky zanikne brány v kolekci vytvořenou testovaným výrazu dotazu (až po a včetně klauzule SELECT). Pokud se všechny modifikátor tyto informace zadané, ne duplicitní vyloučení se provádí; VŠE je výchozí hodnota.  
  
## <a name="differences-from-transact-sql"></a>Rozdíly v Transact-SQL  
 Na rozdíl od příkazů jazyka Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nepodporuje použití * argument v klauzuli SELECT.  Místo toho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje vytvářet dotazy do projektu si celých záznamů pomocí odkazu na kolekci aliasy z klauzule FROM, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT * FROM T1, T2  
```  
  
 Předchozí [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazu dotazu je vyjádřen v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL vyberte operátor, který se používá k určení prvků vrácených dotazem. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Viz také  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
