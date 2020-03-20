---
title: POŘADÍ OD (Entita SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150066"
---
# <a name="order-by-entity-sql"></a>POŘADÍ OD (Entita SQL)
Určuje pořadí řazení použité u objektů vrácených v příkazu SELECT.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a>Argumenty  
 `order_by_expression`  
 Libovolný platný výraz dotazu určující vlastnost, na které se má řadit. Lze zadat více výrazů řazení. Posloupnost výrazů řazení v klauzuli ORDER BY definuje organizaci seřazené sady výsledků.  
  
 COLLATE {collation_name}  
 Určuje, že operace OBJEDNÁNÍ BY má být provedena `collation_name`podle kolace zadané v . COLLATE je použitelná pouze pro řetězcové výrazy.  
  
 ASC  
 Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny vzestupně, od nejnižší hodnoty po nejvyšší hodnotu. Toto nastavení je výchozí.  
  
 DESC  
 Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny v sestupném pořadí, od nejvyšší hodnoty po nejnižší hodnotu.  
  
 Limit`n`  
 Budou vybrány pouze první `n` položky.  
  
 Přeskočit`n`  
 Přeskočí první `n` položky.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule ORDER BY je logicky použita na výsledek klauzule SELECT. Klauzule ORDER BY může odkazovat na položky ve výběrovém seznamu pomocí jejich aliasů. Klauzule ORDER BY může také odkazovat na jiné proměnné, které jsou aktuálně v oboru. Pokud však byla klauzule SELECT zadána s modifikátorem DISTINCT, klauzule ORDER BY může odkazovat pouze na aliasy z klauzule SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Každý výraz v klauzuli ORDER BY musí být vyhodnocen na nějaký typ, který lze porovnat pro objednanou nerovnost (menší než nebo větší než a tak dále). Tyto typy jsou obecně skalární primitiva, jako jsou čísla, řetězce a data. RowTypes srovnatelné typy jsou také pořadí srovnatelné.  
  
 Pokud váš kód iterates přes objednané sady, jiné než pro projekci nejvyšší úrovně, výstup není zaručeno, že jeho pořadí zachována.  

V následujícím vzorku je zaručeno, že objednávka bude zachována:

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

V následujícím dotazu je řazení vnořeného dotazu ignorováno:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Chcete-li mít objednané union, UNION ALL, EXCEPT, nebo INTERSECT operace, použijte následující vzor:  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Klíčová slova s omezeným přístupem  
 Následující klíčová slova musí být uzavřena v `ORDER BY` uvozovkách při použití v klauzuli:  
  
- Kříž  
  
- Plné  
  
- KEY  
  
- LEFT  
  
- Objednávky  
  
- Vnější  
  
- RIGHT  
  
- ROW  
  
- HODNOTA  
  
## <a name="ordering-nested-queries"></a>Řazení vnořených dotazů  
 V rámci entity vnořený výraz lze umístit kdekoli v dotazu; pořadí vnořeného dotazu není zachováno.  

Následující dotaz seřídí výsledky podle příjmení:  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

V následujícím dotazu je řazení vnořeného dotazu ignorováno:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ORDER BY k určení pořadí řazení použitého u objektů vrácených v příkazu SELECT. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a>Viz také

- [Výrazy dotazu](query-expressions-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Přeskočit](skip-entity-sql.md)
- [Limit](limit-entity-sql.md)
- [Top](top-entity-sql.md)
