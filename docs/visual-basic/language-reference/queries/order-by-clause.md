---
title: Order By – klauzule
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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359745"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="56f18-102">Order By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56f18-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="56f18-103">Určuje pořadí řazení pro výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="56f18-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f18-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="56f18-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="56f18-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="56f18-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="56f18-106">Required.</span></span> <span data-ttu-id="56f18-107">Jedno nebo více polí z aktuálního výsledku dotazu, které identifikují způsob řazení vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="56f18-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="56f18-108">Názvy polí musí být odděleny čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="56f18-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="56f18-109">Jednotlivá pole můžete identifikovat ve vzestupném nebo sestupném pořadí pomocí `Ascending` `Descending` klíčových slov nebo.</span><span class="sxs-lookup"><span data-stu-id="56f18-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="56f18-110">Pokud `Ascending` `Descending` není zadáno klíčové slovo or, výchozí pořadí řazení je vzestupné.</span><span class="sxs-lookup"><span data-stu-id="56f18-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="56f18-111">V poli pořadí řazení se předává přednost zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="56f18-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f18-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56f18-112">Remarks</span></span>  
 <span data-ttu-id="56f18-113">`Order By`K řazení výsledků dotazu můžete použít klauzuli.</span><span class="sxs-lookup"><span data-stu-id="56f18-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="56f18-114">`Order By`Klauzule může řadit výsledek jenom na základě proměnné rozsahu pro aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="56f18-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="56f18-115">`Select`Klauzule například zavádí nový obor ve výrazu dotazu s novými proměnnými iterace pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="56f18-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="56f18-116">Proměnné rozsahu definované před `Select` klauzulí v dotazu nejsou k dispozici za `Select` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="56f18-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="56f18-117">Proto pokud chcete výsledky seřadit podle pole, které není v klauzuli k dispozici `Select` , je nutné `Order By` před klauzulí Vložit klauzuli `Select` .</span><span class="sxs-lookup"><span data-stu-id="56f18-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="56f18-118">Příkladem toho, kdy byste to museli udělat, je, že chcete dotaz seřadit podle polí, která se nevrací jako součást výsledku.</span><span class="sxs-lookup"><span data-stu-id="56f18-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="56f18-119">Vzestupné a sestupné řazení pro pole je určeno implementací <xref:System.IComparable> rozhraní pro datový typ pole.</span><span class="sxs-lookup"><span data-stu-id="56f18-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="56f18-120">Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="56f18-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56f18-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="56f18-121">Example</span></span>  
 <span data-ttu-id="56f18-122">Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `book` pro `books` kolekci.</span><span class="sxs-lookup"><span data-stu-id="56f18-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="56f18-123">`Order By`Klauzule seřadí výsledek dotazu podle ceny ve vzestupném pořadí (výchozí nastavení).</span><span class="sxs-lookup"><span data-stu-id="56f18-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="56f18-124">Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="56f18-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="56f18-125">`Select`Klauzule vybere `Title` `Price` vlastnosti a jako hodnoty vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="56f18-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="56f18-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="56f18-126">Example</span></span>  
 <span data-ttu-id="56f18-127">Následující výraz dotazu používá `Order By` klauzuli pro řazení výsledků dotazu podle ceny v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="56f18-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="56f18-128">Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="56f18-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="56f18-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="56f18-129">Example</span></span>  
 <span data-ttu-id="56f18-130">Následující výraz dotazu používá `Select` klauzuli pro výběr názvu knihy, ceny, data publikování a autora.</span><span class="sxs-lookup"><span data-stu-id="56f18-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="56f18-131">Následně naplní `Title` `Price` pole,, `PublishDate` a `Author` proměnné rozsahu pro nový obor.</span><span class="sxs-lookup"><span data-stu-id="56f18-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="56f18-132">`Order By`Klauzule seřadí novou proměnnou rozsahu podle jména autora, názvu knihy a ceny.</span><span class="sxs-lookup"><span data-stu-id="56f18-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="56f18-133">Jednotlivé sloupce jsou seřazené ve výchozím pořadí (vzestupně).</span><span class="sxs-lookup"><span data-stu-id="56f18-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="56f18-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="56f18-134">See also</span></span>

- [<span data-ttu-id="56f18-135">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56f18-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="56f18-136">Dotazy</span><span class="sxs-lookup"><span data-stu-id="56f18-136">Queries</span></span>](index.md)
- [<span data-ttu-id="56f18-137">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="56f18-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="56f18-138">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="56f18-138">From Clause</span></span>](from-clause.md)
