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
ms.openlocfilehash: d4abb5f0b75ae4069c1dbe695a5c810b1f7aa6e1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482594"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="cd078-102">Order By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd078-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="cd078-103">Určuje pořadí řazení výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="cd078-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd078-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd078-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="cd078-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="cd078-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="cd078-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cd078-106">Required.</span></span> <span data-ttu-id="cd078-107">Nejméně jedno pole z aktuální výsledek dotazu, které určují způsob řazení vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="cd078-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="cd078-108">Názvy polí musí být odděleny čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="cd078-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="cd078-109">Každé pole můžete určit, jak seřadit ve vzestupném nebo sestupném pořadí pomocí `Ascending` nebo `Descending` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="cd078-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="cd078-110">Pokud ne `Ascending` nebo `Descending` – klíčové slovo je zadán, je výchozí pořadí řazení vzestupně.</span><span class="sxs-lookup"><span data-stu-id="cd078-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="cd078-111">Pole pořadí řazení přednost zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="cd078-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd078-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd078-112">Remarks</span></span>  
 <span data-ttu-id="cd078-113">Můžete použít `Order By` klauzule řazení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="cd078-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="cd078-114">`Order By` Klauzule můžete řadit pouze výsledek založený na proměnnou rozsahu aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="cd078-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="cd078-115">Například `Select` klauzule zavádí nový obor ve výrazu dotazu s nové proměnné iterace pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="cd078-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="cd078-116">Proměnné definované před v rozsahu `Select` klauzule v dotazu nejsou k dispozici po `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cd078-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="cd078-117">Proto pokud chcete vaše výsledky podle pole, která není k dispozici v pořadí `Select` klauzule, je nutné umístit `Order By` klauzule před `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cd078-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="cd078-118">Jeden příklad, kdy budete muset udělat při chcete seřadit podle polí, které nebudou zobrazeny jako součást výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="cd078-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="cd078-119">Vzestupném a sestupném pořadí pro pole je dáno provádění <xref:System.IComparable> rozhraní pro datový typ pole.</span><span class="sxs-lookup"><span data-stu-id="cd078-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="cd078-120">Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="cd078-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd078-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd078-121">Example</span></span>  
 <span data-ttu-id="cd078-122">Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `book` pro `books` kolekce.</span><span class="sxs-lookup"><span data-stu-id="cd078-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="cd078-123">`Order By` Klauzule výsledku dotazu seřadí podle cena ve vzestupném pořadí (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cd078-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="cd078-124">Knihy se stejnou cenu jsou seřazeny podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd078-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="cd078-125">`Select` Klauzule vybere `Title` a `Price` vlastnosti jako hodnoty vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="cd078-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="cd078-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd078-126">Example</span></span>  
 <span data-ttu-id="cd078-127">Následující dotaz výraz používá `Order By` klauzule výsledku dotazu seřadit cena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd078-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="cd078-128">Knihy se stejnou cenu jsou seřazeny podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd078-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="cd078-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd078-129">Example</span></span>  
 <span data-ttu-id="cd078-130">Následující dotaz používá výraz `Select` klauzule vyberte název knihy, ceny, datum publikování a vytvářet.</span><span class="sxs-lookup"><span data-stu-id="cd078-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="cd078-131">Pak naplní `Title`, `Price`, `PublishDate`, a `Author` pole proměnné rozsahu nového oboru.</span><span class="sxs-lookup"><span data-stu-id="cd078-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="cd078-132">`Order By` Klauzule orders nové proměnné rozsahu jméno autora, název knihy a ceny.</span><span class="sxs-lookup"><span data-stu-id="cd078-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="cd078-133">Každý sloupec je seřazen v pořadí, výchozí (vzestupně).</span><span class="sxs-lookup"><span data-stu-id="cd078-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cd078-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd078-134">See Also</span></span>  
 [<span data-ttu-id="cd078-135">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd078-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="cd078-136">Dotazy</span><span class="sxs-lookup"><span data-stu-id="cd078-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="cd078-137">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="cd078-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="cd078-138">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="cd078-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
