---
title: Typ definice (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 2e068db0ce202c26cad36c8ed7adf0acdfb8e363
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096020"
---
# <a name="type-definitions-entity-sql"></a>Typ definice (Entity SQL)
Definice typu se používá v příkazu deklarace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vložená funkce.  
  
## <a name="remarks"></a>Poznámky  
 Příkaz deklarace pro vložené funkce se skládá z [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) – klíčové slovo, za nímž následuje identifikátor reprezentující název – funkce (například "MyAvg"), za nímž následuje seznam parametrů definice v závorkách (pro například "poplatky Collection(Decimal)").  
  
 Definice seznamu parametrů se skládá z nuly nebo více definic parametrů. Každá definice parametru se skládá z identifikátor (název parametru funkce, například "poplatky") následovaný definicí typu (například "Collection(Decimal)").  
  
 Definice typu může být buď:  
  
-   Typ identifikátoru (například "Int32" nebo "AdventureWorks.Order").  
  
-   Klíčové slovo `COLLECTION` za nímž následuje jiné definice typu v závorkách (například "Collection(AdventureWorks.Order)").  
  
-   Klíčové slovo řádek následovaného seznamem definice vlastností v závorkách (například "Row(x AdventureWorks.Order)"). Definice vlastností, jako mají formát "`identifier type_definition`, `identifier type_definition`;...".  
  
-   Klíčovým slovem REF, za nímž následuje typ identifikátoru v závorkách (například "Ref(AdventureWorks.Order)"). Operátor pro definici typu REF vyžaduje jako argument typu entity. Primitivní typ nelze zadat jako argument.  
  
 Lze také vnořit definice typů (například "kolekce (Row(x Ref(AdventureWorks.Order)))").  
  
 Typ definice možnosti jsou:  
  
-   `IdentifierName supported_type`, nebo  
  
-   `IdentifierName` KOLEKCE (`type_definition`), nebo  
  
-   `IdentifierName` ŘÁDEK (`property_definition`), nebo  
  
-   `IdentifierName` REF (`supported_entity_type`)  
  
 Možnost definice vlastnosti je `IdentifierName type_definition`.  
  
 Podporované typy jsou všechny typy v aktuálním oboru názvů. Patří mezi ně typy primitivem a entity.  
  
 Podporované entitu, kterou najdete typy pouze typy entit v aktuálním oboru názvů. Neobsahují primitivní typy.  
  
## <a name="examples"></a>Příklady  
 Následuje příklad definicí jednoduchého typu.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Následuje příklad definice typu KOLEKCE.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Následuje příklad definice typu řádku.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Následuje příklad definice typu odkazu.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
