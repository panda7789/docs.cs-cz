---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 2010ef9d6fe37e65824cac877074453db1b789db
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319449"
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
Určuje pořadí řazení používané u objektů vrácených v příkazu SELECT.  
  
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
  
## <a name="arguments"></a>Arguments  
 `order_by_expression`  
 Libovolný platný výraz dotazu určující vlastnost, podle které se má řadit. Lze zadat vícenásobné výrazy řazení. Sekvence výrazů řazení v klauzuli ORDER BY definuje organizaci seřazené sady výsledků.  
  
 KOMPLETování {collation_name}  
 Určuje, že operace ORDER by měla být provedena podle kolace zadané v `collation_name`. Klauzuli COLLATE lze použít pouze pro řetězcové výrazy.  
  
 ASC  
 Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny vzestupně, od nejnižší hodnoty po nejvyšší hodnotu. Toto nastavení je výchozí.  
  
 ŘETĚZEC  
 Určuje, že hodnoty v zadané vlastnosti by měly být seřazené v sestupném pořadí, od nejvyšší hodnoty po nejnižší hodnotu.  
  
 OMEZENÍ @no__t – 0  
 Budou vybrány pouze první položky `n`.  
  
 Přeskočit `n`  
 Přeskočí první položky `n`.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule ORDER BY je logicky aplikována na výsledek klauzule SELECT. Klauzule ORDER BY může odkazovat na položky v seznamu SELECT pomocí jejich aliasů. Klauzule ORDER BY může odkazovat také na jiné proměnné, které jsou aktuálně v oboru. Pokud je však klauzule SELECT zadána s modifikátorem DISTINCT, klauzule ORDER BY může odkazovat pouze na aliasy z klauzule SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Každý výraz v klauzuli ORDER BY se musí vyhodnotit na určitý typ, který lze porovnat s seřazenou nerovností (menší než nebo větší než a tak dále). Tyto typy jsou všeobecně skalární primitivní prvky, jako jsou čísla, řetězce a data. RowTypes srovnatelných typů je také porovnatelný z pořadí.  
  
 Pokud váš kód projde seřazenou sadou, která je jiná než pro projekci nejvyšší úrovně, není zaručeno, že se ve výstupu nezachová jeho objednávka.  

V následující ukázce je zaručeno, že bude zachováno pořadí:

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

V následujícím dotazu se pořadí vnořeného dotazu ignoruje:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Pokud chcete mít objednanou operaci SJEDNOCENí, SJEDNOCENí, vyloučení nebo průnik, použijte následující vzor:  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Omezená klíčová slova  
 Při použití v klauzuli `ORDER BY` musí být v uvozovkách uzavřená následující klíčová slova:  
  
- JÍŽDÍ  
  
- KOMPLETNÍ  
  
- KEY  
  
- ZBÝVÁ  
  
- ZA  
  
- VNĚJŠÍ  
  
- Kliknutím  
  
- ROW  
  
- OSA  
  
## <a name="ordering-nested-queries"></a>Řazení vnořených dotazů  
 V Entity Framework vnořený výraz může být umístěn kdekoli v dotazu; pořadí vnořeného dotazu není zachováno.  

Následující dotaz bude seřadit výsledky podle příjmení:  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

V následujícím dotazu se pořadí vnořeného dotazu ignoruje:  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor ORDER BY k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a>Viz také:

- [Výrazy dotazu](query-expressions-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [TOP](top-entity-sql.md)
