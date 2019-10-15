---
title: Definice typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 35f660a66fd706b37187056830af5e06ac586caa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319252"
---
# <a name="type-definitions-entity-sql"></a>Definice typů (Entity SQL)
Definice typu se používá v příkazu deklarace vložené funkce [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="remarks"></a>Poznámky  
 Příkaz deklarace pro vloženou funkci se skládá z klíčového slova [funkce](function-entity-sql.md) následovaného identifikátorem představujícím název funkce (například "MyAvg") následovaným seznamem definic parametrů v závorkách (například "kolekce poplatků ( Decimal) ").  
  
 Seznam definic parametrů se skládá z nuly nebo více definic parametrů. Každá definice parametru se skládá z identifikátoru (název parametru funkce, například "poplatky") následovaný definicí typu (například "Collection (desetinné číslo)").  
  
 Definice typu můžou být buď:  
  
- Typ identifikátoru (například "Int32" nebo "AdventureWorks. Order").  
  
- Klíčové slovo `COLLECTION` následované jinou definicí typu v závorkách (například "Collection (AdventureWorks. Order)").  
  
- ŘÁDEK klíčového slova následovaný seznamem definic vlastností v závorkách (například "řádek (x AdventureWorks. Order)"). Definice vlastností mají formát, jako je například "`identifier type_definition`, `identifier type_definition`,...".  
  
- Klíčové slovo REF následované typem identifikátoru v závorkách (například "ref (AdventureWorks. Order)"). Operátor definice typu REF vyžaduje jako argument typ entity. Jako argument nelze zadat primitivní typ.  
  
 Můžete také vnořovat definice typu (například "Collection" (řádek (# ref (AdventureWorks. Order))) ").  
  
 Možnosti definice typu jsou:  
  
- `IdentifierName supported_type` nebo  
  
- KOLEKCE `IdentifierName` (`type_definition`) nebo  
  
- `IdentifierName` řádek (`property_definition`) nebo  
  
- `IdentifierName` REF (`supported_entity_type`)  
  
 Možnost definice vlastnosti je `IdentifierName type_definition`.  
  
 Podporované typy jsou všechny typy v aktuálním oboru názvů. Mezi ně patří primitivní typy a typy entit.  
  
 Podporované typy entit odkazují pouze na typy entit v aktuálním oboru názvů. Nezahrnují primitivní typy.  
  
## <a name="examples"></a>Příklady  
 Následuje příklad definice jednoduchého typu.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Následuje příklad definice typu kolekce.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Následuje příklad definice typu řádku.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Následuje příklad definice typu REF.  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Reference k Entity SQL](entity-sql-reference.md)
