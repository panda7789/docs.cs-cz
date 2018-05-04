---
title: Definice typů (entita SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7abbe5dfed005a10955a385cadf12725a9450512
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="type-definitions-entity-sql"></a>Definice typů (entita SQL)
Definice typu se používá v deklaraci prohlášení o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vložená funkce.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz deklarace pro vložená funkce se skládá z [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) – klíčové slovo, za nímž následuje identifikátor reprezentující název funkce (například "MyAvg"), za nímž následuje seznam parametrů definice do závorek (pro například "poplatky Collection(Decimal)").  
  
 Definice seznam parametrů se skládá z počtu nula či více definicemi parametrů. Každý definici parametru se skládá z identifikátor (název parametru funkce, například "poplatky") a potom podle definice typu (například "Collection(Decimal)").  
  
 Typ definice může být buď:  
  
-   Typ identifikátoru (například "Int32" nebo "AdventureWorks.Order").  
  
-   Klíčové slovo `COLLECTION` následuje jiné definice typu v závorkách (například "Collection(AdventureWorks.Order)").  
  
-   Klíčové slovo řádek následovaný seznam definic vlastností do závorek (například "Row(x AdventureWorks.Order)"). Definice vlastností mít formátu jako "`identifier type_definition`, `identifier type_definition`,...".  
  
-   Klíčové slovo REF následovaný typem identifikátoru v závorkách (například "Ref(AdventureWorks.Order)"). Operátor definice typu REF vyžaduje jako argument typ entity. Primitivní typ nelze zadat jako argument.  
  
 Můžete také vnořovat definic typů (například "kolekce (Row(x Ref(AdventureWorks.Order)))").  
  
 Typ definice možnosti jsou:  
  
-   `IdentifierName supported_type`, nebo  
  
-   `IdentifierName` KOLEKCE (`type_definition`), nebo  
  
-   `IdentifierName` ŘÁDEK (`property_definition`), nebo  
  
-   `IdentifierName` REF (`supported_entity_type`)  
  
 Možnost definice vlastnost je `IdentifierName type_definition`.  
  
 Podporované typy jsou všechny typy v aktuálním oboru názvů. Mezi ně patří entity i primitivní typy.  
  
 Podporované entity, které typy odkazovat jenom typy entit v aktuálním oboru názvů. Nezahrnujte primitivní typy.  
  
## <a name="examples"></a>Příklady  
 Následuje příklad definici jednoduchého typu.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Následuje příklad definici typu KOLEKCE.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Následuje příklad definici typ řádku.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Následuje příklad definici typu REF.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
