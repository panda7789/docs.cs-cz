---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 4cf65637603fd6c20a33b1ae6ecd8b6ded36a246
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328475"
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
Určuje pořadí řazení použít u objektů vrácených v příkazu SELECT.  
  
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
 Libovolný platný dotaz výraz určující vlastnost, na kterém se má seřadit. Je možné zadat více výrazů řazení. Definuje sekvenci výrazů řazení v klauzuli ORDER by organizace sady seřazených výsledků.  
  
 COLLATE {collation_name}  
 Určuje, že operaci Order by mělo být provedeno řazení zadané v `collation_name`. KOLACE je možné použít pouze řetězcové výrazy.  
  
 ASC  
 Určuje, zda mají být řazeny hodnoty v zadané vlastnosti ve vzestupném pořadí od nejnižší hodnoty po nejvyšší hodnotu. Toto nastavení je výchozí.  
  
 DESC  
 Určuje, že mají být řazeny hodnoty v zadané vlastnosti v sestupném pořadí, v nejvyšší hodnotu na nejnižší hodnotu.  
  
 LIMIT `n`  
 Pouze první `n` budou vybrané položky.  
  
 SKIP `n`  
 Přeskočí první `n` položky.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule ORDER by je logicky použít výsledek výrazu klauzuli SELECT. Klauzule ORDER by může odkazovat položky v seznamu select pomocí jejich aliasy. Klauzule ORDER by může také odkazovat další proměnné, které jsou aktuálně oboru. Ale pokud byl zadán klauzuli SELECT DISTINCT modifikátorem, klauzule ORDER by mohou odkazovat pouze aliasy v klauzuli SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Každý výraz v klauzuli ORDER by musí vyhodnotit na nějaký typ, který je možné porovnat seřazený nerovnost (menší než nebo rovna, a tak dále). Tyto typy jsou obecně skalární primitivních elementů, jako jsou čísla, řetězce a data. RowTypes srovnatelných typů jsou také porovnatelný z hlediska pořadí.  
  
 Pokud váš kód iteruje seřazené sady, jiné než pro nejvyšší úrovně projekce výstup není zaručeno má jeho pořadí zachovány.  
  
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
  
 Pokud chcete mít seřazený UNION, UNION ALL, EXCEPT nebo INTERSECT operace, použijte následující vzor:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Klíčová slova s omezeným přístupem  
 Následující klíčová slova musí být uzavřen v uvozovkách při použití `ORDER BY` klauzule:  
  
-   RŮZNÉ  
  
-   ÚPLNÉ  
  
-   KEY  
  
-   DOLEVA  
  
-   POŘADÍ  
  
-   VNĚJŠÍ  
  
-   DOPRAVA  
  
-   ROW  
  
-   HODNOTA  
  
## <a name="ordering-nested-queries"></a>Řazení vnořené dotazy  
 V rozhraní Entity Framework vnořený výraz může být umístěna kdekoli v dotazu; není zachováno pořadí vnořeného dotazu.  
  
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
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor klauzule ORDER BY k určení pořadí řazení použít u objektů vrácených v příkazu SELECT. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Viz také:

- [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
