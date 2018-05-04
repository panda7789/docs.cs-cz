---
title: Řadit podle (entita SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 5cffd7a696496f92ae83822faff2f08e325eea93
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="order-by-entity-sql"></a>Řadit podle (entita SQL)
Určuje pořadí řazení použít u objektů, vrátí se v příkazu SELECT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a>Arguments  
 `order_by_expression`  
 Jakýkoli platný dotaz výraz zadání vlastnosti, na kterém se má seřadit. Je možné zadat více výrazů řazení. Definuje pořadí řazení výrazů v klauzuli ORDER by organizace ze seřazené sady.  
  
 Klauzuli COLLATE {collation_name}  
 Určuje, že operaci Order by mělo být provedeno řazení zadané v `collation_name`. Klauzuli COLLATE lze použít pouze u řetězců výrazy.  
  
 ASC  
 Určuje, že hodnoty v zadané vlastnosti by měl být seřazeny ve vzestupném pořadí od nejnižší hodnoty po nejvyšší hodnotu. Toto nastavení je výchozí.  
  
 DESC  
 Určuje, že hodnoty v zadané vlastnosti by měl být seřazeny sestupně, z nejvyšší hodnotu s nejnižší hodnotou.  
  
 LIMIT `n`  
 Pouze první `n` budou vybrány položky.  
  
 PŘESKOČIT `n`  
 Přeskočí první `n` položky.  
  
## <a name="remarks"></a>Poznámky  
 Klauzuli ORDER by je logicky použita na výsledek klauzuli SELECT. Klauzuli ORDER by můžete odkazovat na položky v seznamu select pomocí jejich aliasy. Klauzuli ORDER by můžete také odkazovat na jiné proměnné, které jsou aktuálně oboru. Ale pokud se odlišné modifikátor byla zadána klauzule SELECT, klauzuli ORDER by může odkazovat pouze aliasy z klauzule SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Každý výraz v klauzuli ORDER BY se musí vyhodnotit nějaký typ, který je možné porovnávat nerovnost seřazené (je menší než nebo rovna, a tak dále). Tyto typy jsou obecně skalární primitiv například čísla, řetězce a data. RowTypes porovnatelnými typy jsou také porovnatelný z hlediska pořadí.  
  
 Pokud váš kód iteruje nad seřazené sady, jiné než pro projekci nejvyšší úrovně, výstup není zaručena tak, aby měl jeho pořadí zachovaná.  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Pokud chcete mít seřazené UNION, UNION ALL, EXCEPT nebo INTERSECT operace, použijte následující vzor:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Klíčová slova s omezeným přístupem  
 Následující klíčová slova musí být uzavřena v uvozovkách, když se používá v `ORDER BY` klauzule:  
  
-   MEZI  
  
-   ÚPLNÁ  
  
-   KLÍČ  
  
-   VLEVO  
  
-   POŘADÍ  
  
-   VNĚJŠÍ  
  
-   VPRAVO  
  
-   ŘÁDEK  
  
-   HODNOTA  
  
## <a name="ordering-nested-queries"></a>Řazení vnořené dotazy  
 V rozhraní Entity Framework výraz vnořené můžete umístit kdekoli v dotazu; není zachovávané pořadí vnořený dotaz.  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor Order k určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Viz také  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
