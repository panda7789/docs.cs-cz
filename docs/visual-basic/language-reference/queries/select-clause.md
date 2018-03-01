---
title: "Select – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d8cabcbd8554ca2aee639eaac8a52f0485a266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="561d2-102">Select – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="561d2-102">Select Clause (Visual Basic)</span></span>
<span data-ttu-id="561d2-103">Definuje výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="561d2-103">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="561d2-104">Syntax</span></span>  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="561d2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="561d2-105">Parts</span></span>  
 `var1`  
 <span data-ttu-id="561d2-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="561d2-106">Optional.</span></span> <span data-ttu-id="561d2-107">Alias, který slouží k odkazování výsledky sloupcového výrazu.</span><span class="sxs-lookup"><span data-stu-id="561d2-107">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="561d2-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="561d2-108">Required.</span></span> <span data-ttu-id="561d2-109">Název pole, které chcete vrátit ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="561d2-109">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="561d2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="561d2-110">Remarks</span></span>  
 <span data-ttu-id="561d2-111">Můžete použít `Select` klauzule k definování výsledků vrácených z dotazu.</span><span class="sxs-lookup"><span data-stu-id="561d2-111">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="561d2-112">Díky tomu můžete buď zadat členy nové anonymní typ, který je vytvořen pomocí dotazu nebo pro cílové členy s názvem typu, který je vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="561d2-112">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="561d2-113">`Select` Klauzule není nutné pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="561d2-113">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="561d2-114">Pokud žádné `Select` je zadána klauzule, dotaz vrátí typ založený na všechny členy proměnných rozsahu identifikovat v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="561d2-114">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="561d2-115">Další informace najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="561d2-115">For more information, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="561d2-116">Když dotaz vytváří pojmenovaného typu, vrátí výsledek typu <xref:System.Collections.Generic.IEnumerable%601> kde `T` je typ vytvořený.</span><span class="sxs-lookup"><span data-stu-id="561d2-116">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="561d2-117">`Select` Klauzule odkazovat všechny proměnné v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="561d2-117">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="561d2-118">To zahrnuje určené v proměnné rozsahu `From` – klauzule (nebo `From` klauzule).</span><span class="sxs-lookup"><span data-stu-id="561d2-118">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="561d2-119">Zahrnuje také všechny nové proměnné, vytvořené pomocí alias pomocí `Aggregate`, `Let`, `Group By`, nebo `Group Join` klauzule nebo proměnné z předchozí `Select` klauzule ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="561d2-119">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="561d2-120">`Select` Klauzule může také obsahovat statické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="561d2-120">The `Select` clause can also include static values.</span></span> <span data-ttu-id="561d2-121">Například následující příklad kódu ukazuje výrazu dotazu, ve kterém `Select` klauzule definuje výsledek dotazu jako nový anonymní typ s čtyři členy: `ProductName`, `Price`, `Discount`, a `DiscountedPrice`.</span><span class="sxs-lookup"><span data-stu-id="561d2-121">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="561d2-122">`ProductName` a `Price` z proměnnou rozsahu produktu, který je definován v člen hodnot, která `From` klauzule.</span><span class="sxs-lookup"><span data-stu-id="561d2-122">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="561d2-123">`DiscountedPrice` Člen hodnota je vypočítána v `Let` klauzule.</span><span class="sxs-lookup"><span data-stu-id="561d2-123">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="561d2-124">`Discount` Člen je statické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="561d2-124">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 <span data-ttu-id="561d2-125">`Select` Klauzule zavádí novou sadu proměnných rozsahu pro klauzule následné dotazu a předchozí proměnné rozsahu již nejsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="561d2-125">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="561d2-126">Poslední `Select` klauzule ve výrazu dotazu určuje návratová hodnota dotazu.</span><span class="sxs-lookup"><span data-stu-id="561d2-126">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="561d2-127">Například následující dotaz vrátí společnosti název a pořadí ID pro každý zákazníka pořadí, pro který překračuje celkové 500.</span><span class="sxs-lookup"><span data-stu-id="561d2-127">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="561d2-128">První `Select` identifikuje proměnné rozsahu pro klauzuli `Where` klauzule a druhý `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="561d2-128">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="561d2-129">Druhý `Select` klauzule identifikuje hodnot vrácených dotazem jako nový typ anonymní.</span><span class="sxs-lookup"><span data-stu-id="561d2-129">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 <span data-ttu-id="561d2-130">Pokud `Select` klauzule identifikuje jednu položku vrátit, výrazu dotazu vrátí kolekci typ tohoto jednu položku.</span><span class="sxs-lookup"><span data-stu-id="561d2-130">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="561d2-131">Pokud `Select` klauzule identifikuje více položek k vrácení, výrazu dotazu vrátí kolekci nový anonymní typ, a to podle vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="561d2-131">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="561d2-132">Například následující dva dotazy vrátí kolekce dva různé typy na základě `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="561d2-132">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="561d2-133">První dotaz vrátí kolekci názvů společnosti jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="561d2-133">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="561d2-134">Druhý dotaz vrátí kolekci `Customer` objekty naplněný názvy společnosti a informace o adrese.</span><span class="sxs-lookup"><span data-stu-id="561d2-134">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="561d2-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="561d2-135">Example</span></span>  
 <span data-ttu-id="561d2-136">Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `cust` pro `customers` kolekce.</span><span class="sxs-lookup"><span data-stu-id="561d2-136">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="561d2-137">`Select` Klauzule vybere jméno zákazníka a hodnota ID a naplní `CompanyName` a `CustomerID` sloupce novou proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="561d2-137">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="561d2-138">`For Each` Příkaz cyklicky prochází přes každý vrácený objekt a zobrazí se `CompanyName` a `CustomerID` sloupců pro každý záznam.</span><span class="sxs-lookup"><span data-stu-id="561d2-138">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="561d2-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="561d2-139">See Also</span></span>  
 [<span data-ttu-id="561d2-140">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="561d2-140">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="561d2-141">Dotazy</span><span class="sxs-lookup"><span data-stu-id="561d2-141">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="561d2-142">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="561d2-142">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="561d2-143">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="561d2-143">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="561d2-144">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="561d2-144">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="561d2-145">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="561d2-145">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
