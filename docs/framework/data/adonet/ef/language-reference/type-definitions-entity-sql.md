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
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="7d324-102">Definice typů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7d324-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="7d324-103">Definice typu se používá v příkazu deklarace vložené funkce [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d324-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d324-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d324-104">Remarks</span></span>  
 <span data-ttu-id="7d324-105">Příkaz deklarace pro vloženou funkci se skládá z klíčového slova [funkce](function-entity-sql.md) následovaného identifikátorem představujícím název funkce (například "MyAvg") následovaným seznamem definic parametrů v závorkách (například "kolekce poplatků ( Decimal) ").</span><span class="sxs-lookup"><span data-stu-id="7d324-105">The declaration statement for an inline function consists of the [FUNCTION](function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="7d324-106">Seznam definic parametrů se skládá z nuly nebo více definic parametrů.</span><span class="sxs-lookup"><span data-stu-id="7d324-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="7d324-107">Každá definice parametru se skládá z identifikátoru (název parametru funkce, například "poplatky") následovaný definicí typu (například "Collection (desetinné číslo)").</span><span class="sxs-lookup"><span data-stu-id="7d324-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="7d324-108">Definice typu můžou být buď:</span><span class="sxs-lookup"><span data-stu-id="7d324-108">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="7d324-109">Typ identifikátoru (například "Int32" nebo "AdventureWorks. Order").</span><span class="sxs-lookup"><span data-stu-id="7d324-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="7d324-110">Klíčové slovo `COLLECTION` následované jinou definicí typu v závorkách (například "Collection (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="7d324-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="7d324-111">ŘÁDEK klíčového slova následovaný seznamem definic vlastností v závorkách (například "řádek (x AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="7d324-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="7d324-112">Definice vlastností mají formát, jako je například "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="7d324-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="7d324-113">Klíčové slovo REF následované typem identifikátoru v závorkách (například "ref (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="7d324-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="7d324-114">Operátor definice typu REF vyžaduje jako argument typ entity.</span><span class="sxs-lookup"><span data-stu-id="7d324-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="7d324-115">Jako argument nelze zadat primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="7d324-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="7d324-116">Můžete také vnořovat definice typu (například "Collection" (řádek (# ref (AdventureWorks. Order))) ").</span><span class="sxs-lookup"><span data-stu-id="7d324-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="7d324-117">Možnosti definice typu jsou:</span><span class="sxs-lookup"><span data-stu-id="7d324-117">The type definition options are:</span></span>  
  
- <span data-ttu-id="7d324-118">`IdentifierName supported_type` nebo</span><span class="sxs-lookup"><span data-stu-id="7d324-118">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="7d324-119">KOLEKCE `IdentifierName` (`type_definition`) nebo</span><span class="sxs-lookup"><span data-stu-id="7d324-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="7d324-120">`IdentifierName` řádek (`property_definition`) nebo</span><span class="sxs-lookup"><span data-stu-id="7d324-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="7d324-121">`IdentifierName` REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="7d324-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="7d324-122">Možnost definice vlastnosti je `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="7d324-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="7d324-123">Podporované typy jsou všechny typy v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d324-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="7d324-124">Mezi ně patří primitivní typy a typy entit.</span><span class="sxs-lookup"><span data-stu-id="7d324-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="7d324-125">Podporované typy entit odkazují pouze na typy entit v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d324-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="7d324-126">Nezahrnují primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="7d324-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7d324-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="7d324-127">Examples</span></span>  
 <span data-ttu-id="7d324-128">Následuje příklad definice jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="7d324-128">The following is an example of a simple type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="7d324-129">Následuje příklad definice typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="7d324-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="7d324-130">Následuje příklad definice typu řádku.</span><span class="sxs-lookup"><span data-stu-id="7d324-130">The following is an example of a ROW type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="7d324-131">Následuje příklad definice typu REF.</span><span class="sxs-lookup"><span data-stu-id="7d324-131">The following is an example of a REF type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d324-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d324-132">See also</span></span>

- [<span data-ttu-id="7d324-133">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7d324-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="7d324-134">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7d324-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
