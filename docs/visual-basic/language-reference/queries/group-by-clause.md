---
title: Group By – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 87080254ad5d237a593f0c35e7c3fdaef3a8ad59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350479"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="882d0-102">Group By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="882d0-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="882d0-103">Groups the elements of a query result.</span><span class="sxs-lookup"><span data-stu-id="882d0-103">Groups the elements of a query result.</span></span> <span data-ttu-id="882d0-104">Can also be used to apply aggregate functions to each group.</span><span class="sxs-lookup"><span data-stu-id="882d0-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="882d0-105">The grouping operation is based on one or more keys.</span><span class="sxs-lookup"><span data-stu-id="882d0-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882d0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="882d0-106">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="882d0-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="882d0-107">Parts</span></span>  
  
- <span data-ttu-id="882d0-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="882d0-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="882d0-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="882d0-109">Optional.</span></span> <span data-ttu-id="882d0-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span><span class="sxs-lookup"><span data-stu-id="882d0-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="882d0-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span><span class="sxs-lookup"><span data-stu-id="882d0-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="882d0-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="882d0-112">Required.</span></span> <span data-ttu-id="882d0-113">An expression that identifies the key to use to determine the groups of elements.</span><span class="sxs-lookup"><span data-stu-id="882d0-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="882d0-114">You can specify more than one key to specify a composite key.</span><span class="sxs-lookup"><span data-stu-id="882d0-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="882d0-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="882d0-115">Optional.</span></span> <span data-ttu-id="882d0-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span><span class="sxs-lookup"><span data-stu-id="882d0-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="882d0-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="882d0-117">Required.</span></span> <span data-ttu-id="882d0-118">One or more expressions that identify how the groups are aggregated.</span><span class="sxs-lookup"><span data-stu-id="882d0-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="882d0-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span><span class="sxs-lookup"><span data-stu-id="882d0-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="882d0-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="882d0-120">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="882d0-121">You can also include aggregate functions to apply to the group.</span><span class="sxs-lookup"><span data-stu-id="882d0-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="882d0-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="882d0-122">Remarks</span></span>  
 <span data-ttu-id="882d0-123">You can use the `Group By` clause to break the results of a query into groups.</span><span class="sxs-lookup"><span data-stu-id="882d0-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="882d0-124">The grouping is based on a key or a composite key consisting of multiple keys.</span><span class="sxs-lookup"><span data-stu-id="882d0-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="882d0-125">Elements that are associated with matching key values are included in the same group.</span><span class="sxs-lookup"><span data-stu-id="882d0-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="882d0-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span><span class="sxs-lookup"><span data-stu-id="882d0-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="882d0-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span><span class="sxs-lookup"><span data-stu-id="882d0-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="882d0-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="882d0-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="882d0-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="882d0-129">Example</span></span>  
 <span data-ttu-id="882d0-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span><span class="sxs-lookup"><span data-stu-id="882d0-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="882d0-131">The results are ordered by country/region name.</span><span class="sxs-lookup"><span data-stu-id="882d0-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="882d0-132">The grouped results are ordered by city name.</span><span class="sxs-lookup"><span data-stu-id="882d0-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="882d0-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="882d0-133">See also</span></span>

- [<span data-ttu-id="882d0-134">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="882d0-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="882d0-135">Dotazy</span><span class="sxs-lookup"><span data-stu-id="882d0-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="882d0-136">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="882d0-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="882d0-137">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="882d0-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="882d0-138">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="882d0-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="882d0-139">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="882d0-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="882d0-140">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="882d0-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
