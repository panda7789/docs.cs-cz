---
title: "Definice typů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b890a56daeab1c3a0fbb8c95ec29a81cb7689e9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="3caa5-102">Definice typů (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="3caa5-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="3caa5-103">Definice typu se používá v deklaraci prohlášení o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vložená funkce.</span><span class="sxs-lookup"><span data-stu-id="3caa5-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3caa5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3caa5-104">Remarks</span></span>  
 <span data-ttu-id="3caa5-105">Příkaz deklarace pro vložená funkce se skládá z [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) – klíčové slovo, za nímž následuje identifikátor reprezentující název funkce (například "MyAvg"), za nímž následuje seznam parametrů definice do závorek (pro například "poplatky Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="3caa5-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="3caa5-106">Definice seznam parametrů se skládá z počtu nula či více definicemi parametrů.</span><span class="sxs-lookup"><span data-stu-id="3caa5-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="3caa5-107">Každý definici parametru se skládá z identifikátor (název parametru funkce, například "poplatky") a potom podle definice typu (například "Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="3caa5-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="3caa5-108">Typ definice může být buď:</span><span class="sxs-lookup"><span data-stu-id="3caa5-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="3caa5-109">Typ identifikátoru (například "Int32" nebo "AdventureWorks.Order").</span><span class="sxs-lookup"><span data-stu-id="3caa5-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="3caa5-110">Klíčové slovo `COLLECTION` následuje jiné definice typu v závorkách (například "Collection(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="3caa5-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="3caa5-111">Klíčové slovo řádek následovaný seznam definic vlastností do závorek (například "Row(x AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="3caa5-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="3caa5-112">Definice vlastností mít formátu jako "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="3caa5-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="3caa5-113">Klíčové slovo REF následovaný typem identifikátoru v závorkách (například "Ref(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="3caa5-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="3caa5-114">Operátor definice typu REF vyžaduje jako argument typ entity.</span><span class="sxs-lookup"><span data-stu-id="3caa5-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="3caa5-115">Primitivní typ nelze zadat jako argument.</span><span class="sxs-lookup"><span data-stu-id="3caa5-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="3caa5-116">Můžete také vnořovat definic typů (například "kolekce (Row(x Ref(AdventureWorks.Order)))").</span><span class="sxs-lookup"><span data-stu-id="3caa5-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="3caa5-117">Typ definice možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="3caa5-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="3caa5-118">`IdentifierName supported_type`, nebo</span><span class="sxs-lookup"><span data-stu-id="3caa5-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="3caa5-119">`IdentifierName`KOLEKCE (`type_definition`), nebo</span><span class="sxs-lookup"><span data-stu-id="3caa5-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="3caa5-120">`IdentifierName`ŘÁDEK (`property_definition`), nebo</span><span class="sxs-lookup"><span data-stu-id="3caa5-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="3caa5-121">`IdentifierName`REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="3caa5-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="3caa5-122">Možnost definice vlastnost je `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="3caa5-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="3caa5-123">Podporované typy jsou všechny typy v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3caa5-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="3caa5-124">Mezi ně patří entity i primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="3caa5-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="3caa5-125">Podporované entity, které typy odkazovat jenom typy entit v aktuálním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3caa5-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="3caa5-126">Nezahrnujte primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="3caa5-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3caa5-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="3caa5-127">Examples</span></span>  
 <span data-ttu-id="3caa5-128">Následuje příklad definici jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="3caa5-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="3caa5-129">Následuje příklad definici typu KOLEKCE.</span><span class="sxs-lookup"><span data-stu-id="3caa5-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="3caa5-130">Následuje příklad definici typ řádku.</span><span class="sxs-lookup"><span data-stu-id="3caa5-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="3caa5-131">Následuje příklad definici typu REF.</span><span class="sxs-lookup"><span data-stu-id="3caa5-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="3caa5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3caa5-132">See Also</span></span>  
 [<span data-ttu-id="3caa5-133">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="3caa5-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="3caa5-134">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="3caa5-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
