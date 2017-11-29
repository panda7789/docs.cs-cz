---
title: "Order By – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ee21942b966668a67b14aba72b8f9fc5ee903c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="8fc6f-102">Order By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="8fc6f-103">Určuje pořadí řazení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc6f-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="8fc6f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8fc6f-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="8fc6f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-106">Required.</span></span> <span data-ttu-id="8fc6f-107">Minimálně jedno pole z aktuální výsledek dotazu, které zjišťují, jak pořadí vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="8fc6f-108">Názvy polí musí být oddělené čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="8fc6f-109">Každé pole můžete identifikovat jako seřazený ve vzestupném nebo sestupném pořadí pomocí `Ascending` nebo `Descending` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="8fc6f-110">Pokud žádné `Ascending` nebo `Descending` je zadané klíčové slovo, je vzestupné výchozí pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="8fc6f-111">Pole pořadí řazení mají přednost před zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fc6f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fc6f-112">Remarks</span></span>  
 <span data-ttu-id="8fc6f-113">Můžete použít `Order By` klauzule k řazení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="8fc6f-114">`Order By` Klauzule může seřadit pouze výsledku založené na proměnnou rozsahu pro aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="8fc6f-115">Například `Select` klauzule zavádí nový obor ve výrazu dotazu s nové proměnné iterace pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="8fc6f-116">Proměnné definované před v rozsahu `Select` klauzuli v dotazu nejsou k dispozici po `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="8fc6f-117">Proto pokud chcete výsledky podle pole, která není k dispozici v pořadí `Select` klauzule, musíte umístit `Order By` klauzule před `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="8fc6f-118">Jedna je například pokud bude potřeba to udělat v případě, že chcete seřadit podle pole, které nejsou v rámci výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="8fc6f-119">Vzestupné a sestupném pořadí pro pole je dáno implementace <xref:System.IComparable> rozhraní pro datový typ pole.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="8fc6f-120">Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení je ignorována.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc6f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fc6f-121">Example</span></span>  
 <span data-ttu-id="8fc6f-122">Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `book` pro `books` kolekce.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="8fc6f-123">`Order By` Klauzule seřadí výsledek dotazu podle ceny ve vzestupném pořadí (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="8fc6f-124">Knih za stejnou cenu. jsou seřazené podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="8fc6f-125">`Select` Klauzule vybere `Title` a `Price` vlastnosti jako hodnoty vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="8fc6f-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fc6f-126">Example</span></span>  
 <span data-ttu-id="8fc6f-127">Následující dotaz výraz používá `Order By` klauzule výsledek dotazu seřadit cenu v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="8fc6f-128">Knih za stejnou cenu. jsou seřazené podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="8fc6f-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fc6f-129">Example</span></span>  
 <span data-ttu-id="8fc6f-130">Následující dotaz výraz používá `Select` klauzule vyberte název adresáře, cena, publikovat data a vytvářet.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="8fc6f-131">Pak naplní `Title`, `Price`, `PublishDate`, a `Author` pole proměnnou rozsahu nového oboru.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="8fc6f-132">`Order By` Klauzule řadí nové proměnné rozsahu jméno autora, název knihy a ceny.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="8fc6f-133">Každý sloupec je seřazen v pořadí (vzestupně).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8fc6f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fc6f-134">See Also</span></span>  
 [<span data-ttu-id="8fc6f-135">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8fc6f-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="8fc6f-136">Dotazy</span><span class="sxs-lookup"><span data-stu-id="8fc6f-136">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="8fc6f-137">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="8fc6f-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="8fc6f-138">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="8fc6f-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
