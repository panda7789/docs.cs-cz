---
title: Order By – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835008"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="6a089-102">Order By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a089-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="6a089-103">Určuje pořadí řazení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a089-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a089-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a089-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="6a089-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6a089-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="6a089-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6a089-106">Required.</span></span> <span data-ttu-id="6a089-107">Nejméně jedno pole z aktuální výsledek dotazu, které určují způsob řazení vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="6a089-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="6a089-108">Názvy polí musí být odděleny čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="6a089-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="6a089-109">Každé pole můžete určit, jak seřadit ve vzestupném nebo sestupném pořadí pomocí `Ascending` nebo `Descending` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="6a089-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="6a089-110">Pokud ne `Ascending` nebo `Descending` – klíčové slovo je zadán, je výchozí pořadí řazení vzestupně.</span><span class="sxs-lookup"><span data-stu-id="6a089-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="6a089-111">Pole pořadí řazení přednost zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="6a089-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a089-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a089-112">Remarks</span></span>  
 <span data-ttu-id="6a089-113">Můžete použít `Order By` klauzule řazení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a089-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="6a089-114">`Order By` Klauzule můžete řadit pouze výsledek založený na proměnnou rozsahu aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="6a089-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="6a089-115">Například `Select` klauzule zavádí nový obor ve výrazu dotazu s nové proměnné iterace pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="6a089-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="6a089-116">Proměnné definované před v rozsahu `Select` klauzule v dotazu nejsou k dispozici po `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6a089-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="6a089-117">Proto pokud chcete vaše výsledky podle pole, která není k dispozici v pořadí `Select` klauzule, je nutné umístit `Order By` klauzule před `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6a089-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="6a089-118">Jeden příklad, kdy budete muset udělat při chcete seřadit podle polí, které nebudou zobrazeny jako součást výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a089-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="6a089-119">Vzestupném a sestupném pořadí pro pole je dáno provádění <xref:System.IComparable> rozhraní pro datový typ pole.</span><span class="sxs-lookup"><span data-stu-id="6a089-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="6a089-120">Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="6a089-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a089-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a089-121">Example</span></span>  
 <span data-ttu-id="6a089-122">Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `book` pro `books` kolekce.</span><span class="sxs-lookup"><span data-stu-id="6a089-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="6a089-123">`Order By` Klauzule výsledku dotazu seřadí podle cena ve vzestupném pořadí (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6a089-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="6a089-124">Knihy se stejnou cenu jsou seřazeny podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6a089-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="6a089-125">`Select` Klauzule vybere `Title` a `Price` vlastnosti jako hodnoty vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="6a089-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="6a089-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a089-126">Example</span></span>  
 <span data-ttu-id="6a089-127">Následující dotaz výraz používá `Order By` klauzule výsledku dotazu seřadit cena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6a089-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="6a089-128">Knihy se stejnou cenu jsou seřazeny podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6a089-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="6a089-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a089-129">Example</span></span>  
 <span data-ttu-id="6a089-130">Následující dotaz používá výraz `Select` klauzule vyberte název knihy, ceny, datum publikování a vytvářet.</span><span class="sxs-lookup"><span data-stu-id="6a089-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="6a089-131">Pak naplní `Title`, `Price`, `PublishDate`, a `Author` pole proměnné rozsahu nového oboru.</span><span class="sxs-lookup"><span data-stu-id="6a089-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="6a089-132">`Order By` Klauzule orders nové proměnné rozsahu jméno autora, název knihy a ceny.</span><span class="sxs-lookup"><span data-stu-id="6a089-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="6a089-133">Každý sloupec je seřazen v pořadí, výchozí (vzestupně).</span><span class="sxs-lookup"><span data-stu-id="6a089-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="6a089-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a089-134">See also</span></span>

- [<span data-ttu-id="6a089-135">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a089-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6a089-136">Dotazy</span><span class="sxs-lookup"><span data-stu-id="6a089-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="6a089-137">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="6a089-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="6a089-138">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="6a089-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
