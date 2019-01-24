---
title: Typ definice (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7ac27c3dd43cb83272bff991dbd713e8269ccbb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743527"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="74a75-102">Typ definice (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="74a75-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="74a75-103">Definice typu se používá v příkazu deklarace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vložená funkce.</span><span class="sxs-lookup"><span data-stu-id="74a75-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74a75-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74a75-104">Remarks</span></span>  
 <span data-ttu-id="74a75-105">Příkaz deklarace pro vložené funkce se skládá z [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) – klíčové slovo, za nímž následuje identifikátor reprezentující název – funkce (například "MyAvg"), za nímž následuje seznam parametrů definice v závorkách (pro například "poplatky Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="74a75-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="74a75-106">Definice seznamu parametrů se skládá z nuly nebo více definic parametrů.</span><span class="sxs-lookup"><span data-stu-id="74a75-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="74a75-107">Každá definice parametru se skládá z identifikátor (název parametru funkce, například "poplatky") následovaný definicí typu (například "Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="74a75-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="74a75-108">Definice typu může být buď:</span><span class="sxs-lookup"><span data-stu-id="74a75-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="74a75-109">Typ identifikátoru (například "Int32" nebo "AdventureWorks.Order").</span><span class="sxs-lookup"><span data-stu-id="74a75-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="74a75-110">Klíčové slovo `COLLECTION` za nímž následuje jiné definice typu v závorkách (například "Collection(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="74a75-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="74a75-111">Klíčové slovo řádek následovaného seznamem definice vlastností v závorkách (například "Row(x AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="74a75-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="74a75-112">Definice vlastností, jako mají formát "`identifier type_definition`, `identifier type_definition`;...".</span><span class="sxs-lookup"><span data-stu-id="74a75-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="74a75-113">Klíčovým slovem REF, za nímž následuje typ identifikátoru v závorkách (například "Ref(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="74a75-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="74a75-114">Operátor pro definici typu REF vyžaduje jako argument typu entity.</span><span class="sxs-lookup"><span data-stu-id="74a75-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="74a75-115">Primitivní typ nelze zadat jako argument.</span><span class="sxs-lookup"><span data-stu-id="74a75-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="74a75-116">Lze také vnořit definice typů (například "kolekce (Row(x Ref(AdventureWorks.Order)))").</span><span class="sxs-lookup"><span data-stu-id="74a75-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="74a75-117">Typ definice možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="74a75-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="74a75-118">`IdentifierName supported_type`, nebo</span><span class="sxs-lookup"><span data-stu-id="74a75-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="74a75-119">`IdentifierName` KOLEKCE (`type_definition`), nebo</span><span class="sxs-lookup"><span data-stu-id="74a75-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="74a75-120">`IdentifierName` ŘÁDEK (`property_definition`), nebo</span><span class="sxs-lookup"><span data-stu-id="74a75-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="74a75-121">`IdentifierName` REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="74a75-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="74a75-122">Možnost definice vlastnosti je `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="74a75-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="74a75-123">Podporované typy jsou všechny typy v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74a75-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="74a75-124">Patří mezi ně typy primitivem a entity.</span><span class="sxs-lookup"><span data-stu-id="74a75-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="74a75-125">Podporované entitu, kterou najdete typy pouze typy entit v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74a75-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="74a75-126">Neobsahují primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="74a75-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="74a75-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="74a75-127">Examples</span></span>  
 <span data-ttu-id="74a75-128">Následuje příklad definicí jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="74a75-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="74a75-129">Následuje příklad definice typu KOLEKCE.</span><span class="sxs-lookup"><span data-stu-id="74a75-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="74a75-130">Následuje příklad definice typu řádku.</span><span class="sxs-lookup"><span data-stu-id="74a75-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="74a75-131">Následuje příklad definice typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="74a75-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="74a75-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a75-132">See also</span></span>
- [<span data-ttu-id="74a75-133">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74a75-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="74a75-134">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74a75-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
