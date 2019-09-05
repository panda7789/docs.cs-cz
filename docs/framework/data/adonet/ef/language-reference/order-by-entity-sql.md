---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: f3310274766ff3619604e30bfb5f5ca437cb1acd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249755"
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
Určuje pořadí řazení používané u objektů vrácených v příkazu SELECT.  
  
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
 Libovolný platný výraz dotazu určující vlastnost, podle které se má řadit. Lze zadat vícenásobné výrazy řazení. Sekvence výrazů řazení v klauzuli ORDER BY definuje organizaci seřazené sady výsledků.  
  
 KOMPLETování {collation_name}  
 Určuje, že operace ORDER by měla být provedena podle kolace zadané v `collation_name`. Klauzuli COLLATE lze použít pouze pro řetězcové výrazy.  
  
 ASC  
 Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny vzestupně, od nejnižší hodnoty po nejvyšší hodnotu. Toto nastavení je výchozí.  
  
 DESC  
 Určuje, že hodnoty v zadané vlastnosti by měly být seřazené v sestupném pořadí, od nejvyšší hodnoty po nejnižší hodnotu.  
  
 POČTU`n`  
 Budou vybrány pouze `n` první položky.  
  
 PŘÍMO`n`  
 Přeskočí první `n` položky.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule ORDER BY je logicky aplikována na výsledek klauzule SELECT. Klauzule ORDER BY může odkazovat na položky v seznamu SELECT pomocí jejich aliasů. Klauzule ORDER BY může odkazovat také na jiné proměnné, které jsou aktuálně v oboru. Pokud je však klauzule SELECT zadána s modifikátorem DISTINCT, klauzule ORDER BY může odkazovat pouze na aliasy z klauzule SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Každý výraz v klauzuli ORDER BY se musí vyhodnotit na určitý typ, který lze porovnat s seřazenou nerovností (menší než nebo větší než a tak dále). Tyto typy jsou všeobecně skalární primitivní prvky, jako jsou čísla, řetězce a data. RowTypes srovnatelných typů je také porovnatelný z pořadí.  
  
 Pokud váš kód projde seřazenou sadou, která je jiná než pro projekci nejvyšší úrovně, není zaručeno, že se ve výstupu nezachová jeho objednávka.  
  
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
  
 Pokud chcete mít objednanou operaci SJEDNOCENí, SJEDNOCENí, vyloučení nebo průnik, použijte následující vzor:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Omezená klíčová slova  
 Při použití v `ORDER BY` klauzuli musí být v uvozovkách uzavřená následující klíčová slova:  
  
- JÍŽDÍ  
  
- KOMPLETNÍ  
  
- KEY  
  
- ZBÝVÁ  
  
- ZA  
  
- VNĚJŠÍ  
  
- KLIKNUTÍM  
  
- ROW  
  
- OSA  
  
## <a name="ordering-nested-queries"></a>Řazení vnořených dotazů  
 V Entity Framework vnořený výraz může být umístěn kdekoli v dotazu; pořadí vnořeného dotazu není zachováno.  
  
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
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ORDER by k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Viz také:

- [Výrazy dotazu](query-expressions-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [TOP](top-entity-sql.md)
