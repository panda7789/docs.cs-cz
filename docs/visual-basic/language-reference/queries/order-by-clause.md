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
ms.openlocfilehash: f8ee46b12e84f99629c3a92057fc3a7bb8a3c2e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004952"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="d6e8d-102">Order By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6e8d-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="d6e8d-103">Určuje pořadí řazení pro výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6e8d-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d6e8d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d6e8d-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="d6e8d-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-106">Required.</span></span> <span data-ttu-id="d6e8d-107">Jedno nebo více polí z aktuálního výsledku dotazu, které identifikují způsob řazení vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="d6e8d-108">Názvy polí musí být odděleny čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="d6e8d-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="d6e8d-109">Každé pole můžete identifikovat ve vzestupném nebo sestupném pořadí pomocí klíčových slov `Ascending` nebo `Descending`.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="d6e8d-110">Pokud není zadané žádné klíčové slovo `Ascending` nebo `Descending`, výchozí pořadí řazení je vzestupné.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="d6e8d-111">V poli pořadí řazení se předává přednost zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6e8d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6e8d-112">Remarks</span></span>  
 <span data-ttu-id="d6e8d-113">K řazení výsledků dotazu můžete použít klauzuli `Order By`.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="d6e8d-114">Klauzule `Order By` může řadit výsledek jenom na základě proměnné rozsahu pro aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="d6e8d-115">Například klauzule `Select` zavádí nový obor ve výrazu dotazu s novými proměnnými iterace pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="d6e8d-116">Proměnné rozsahu definované před klauzulí `Select` v dotazu nejsou k dispozici po klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="d6e8d-117">Proto pokud chcete výsledky seřadit podle pole, které není k dispozici v klauzuli `Select`, je nutné před klauzulí `Select` Vložit klauzuli `Order By`.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="d6e8d-118">Příkladem toho, kdy byste to museli udělat, je, že chcete dotaz seřadit podle polí, která se nevrací jako součást výsledku.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="d6e8d-119">Vzestupné a sestupné řazení pro pole je určeno implementací rozhraní @no__t 0 pro datový typ pole.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="d6e8d-120">Pokud datový typ neimplementuje rozhraní <xref:System.IComparable>, pořadí řazení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6e8d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6e8d-121">Example</span></span>  
 <span data-ttu-id="d6e8d-122">Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `book` pro kolekci `books`.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="d6e8d-123">Klauzule `Order By` seřadí výsledek dotazu podle ceny ve vzestupném pořadí (výchozí nastavení).</span><span class="sxs-lookup"><span data-stu-id="d6e8d-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="d6e8d-124">Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="d6e8d-125">Klauzule `Select` vybere vlastnosti `Title` a `Price` jako hodnoty vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="d6e8d-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6e8d-126">Example</span></span>  
 <span data-ttu-id="d6e8d-127">Následující výraz dotazu používá klauzuli `Order By` pro řazení výsledků dotazu podle ceny v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="d6e8d-128">Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="d6e8d-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6e8d-129">Example</span></span>  
 <span data-ttu-id="d6e8d-130">Následující výraz dotazu používá klauzuli @no__t 0 pro výběr názvu knihy, ceny, data publikování a autora.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="d6e8d-131">Pak naplní pole `Title`, `Price`, `PublishDate` a `Author` proměnné rozsahu pro nový obor.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="d6e8d-132">Klauzule `Order By` seřadí novou proměnnou rozsahu podle jména autora, názvu knihy a ceny.</span><span class="sxs-lookup"><span data-stu-id="d6e8d-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="d6e8d-133">Jednotlivé sloupce jsou seřazené ve výchozím pořadí (vzestupně).</span><span class="sxs-lookup"><span data-stu-id="d6e8d-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="d6e8d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6e8d-134">See also</span></span>

- [<span data-ttu-id="d6e8d-135">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6e8d-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d6e8d-136">Dotazy</span><span class="sxs-lookup"><span data-stu-id="d6e8d-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d6e8d-137">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="d6e8d-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="d6e8d-138">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="d6e8d-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
