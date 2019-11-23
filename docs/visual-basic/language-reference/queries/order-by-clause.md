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
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350415"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="ad2de-102">Order By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad2de-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="ad2de-103">Specifies the sort order for a query result.</span><span class="sxs-lookup"><span data-stu-id="ad2de-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad2de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad2de-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ad2de-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ad2de-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="ad2de-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ad2de-106">Required.</span></span> <span data-ttu-id="ad2de-107">One or more fields from the current query result that identify how to order the returned values.</span><span class="sxs-lookup"><span data-stu-id="ad2de-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="ad2de-108">The field names must be separated by commas (,).</span><span class="sxs-lookup"><span data-stu-id="ad2de-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="ad2de-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span><span class="sxs-lookup"><span data-stu-id="ad2de-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="ad2de-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span><span class="sxs-lookup"><span data-stu-id="ad2de-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="ad2de-111">The sort order fields are given precedence from left to right.</span><span class="sxs-lookup"><span data-stu-id="ad2de-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad2de-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad2de-112">Remarks</span></span>  
 <span data-ttu-id="ad2de-113">You can use the `Order By` clause to sort the results of a query.</span><span class="sxs-lookup"><span data-stu-id="ad2de-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="ad2de-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span><span class="sxs-lookup"><span data-stu-id="ad2de-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="ad2de-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span><span class="sxs-lookup"><span data-stu-id="ad2de-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="ad2de-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="ad2de-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="ad2de-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="ad2de-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="ad2de-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span><span class="sxs-lookup"><span data-stu-id="ad2de-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="ad2de-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span><span class="sxs-lookup"><span data-stu-id="ad2de-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="ad2de-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span><span class="sxs-lookup"><span data-stu-id="ad2de-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad2de-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad2de-121">Example</span></span>  
 <span data-ttu-id="ad2de-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span><span class="sxs-lookup"><span data-stu-id="ad2de-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="ad2de-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span><span class="sxs-lookup"><span data-stu-id="ad2de-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="ad2de-124">Books with the same price are sorted by title in ascending order.</span><span class="sxs-lookup"><span data-stu-id="ad2de-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="ad2de-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span><span class="sxs-lookup"><span data-stu-id="ad2de-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="ad2de-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad2de-126">Example</span></span>  
 <span data-ttu-id="ad2de-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span><span class="sxs-lookup"><span data-stu-id="ad2de-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="ad2de-128">Books with the same price are sorted by title in ascending order.</span><span class="sxs-lookup"><span data-stu-id="ad2de-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="ad2de-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad2de-129">Example</span></span>  
 <span data-ttu-id="ad2de-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span><span class="sxs-lookup"><span data-stu-id="ad2de-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="ad2de-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span><span class="sxs-lookup"><span data-stu-id="ad2de-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="ad2de-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span><span class="sxs-lookup"><span data-stu-id="ad2de-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="ad2de-133">Each column is sorted in the default order (ascending).</span><span class="sxs-lookup"><span data-stu-id="ad2de-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="ad2de-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad2de-134">See also</span></span>

- [<span data-ttu-id="ad2de-135">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad2de-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ad2de-136">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ad2de-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ad2de-137">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="ad2de-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ad2de-138">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="ad2de-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
