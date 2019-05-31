---
title: Group By – klauzule (Visual Basic)
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
ms.openlocfilehash: 04378d2c9a7e565343ff663997e2a3e61f04f9d2
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423573"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="264f2-102">Group By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="264f2-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="264f2-103">Seskupuje prvky sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="264f2-103">Groups the elements of a query result.</span></span> <span data-ttu-id="264f2-104">Můžete také použít k aplikaci agregačních funkcí na každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="264f2-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="264f2-105">Operace seskupení je založená na jeden nebo více klíčů.</span><span class="sxs-lookup"><span data-stu-id="264f2-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="264f2-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="264f2-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="264f2-107">Parts</span></span>  
  
- <span data-ttu-id="264f2-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="264f2-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="264f2-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="264f2-109">Optional.</span></span> <span data-ttu-id="264f2-110">Jedno nebo více polí proměnné dotazu nebo proměnné, které explicitně určete pole, které mají být zahrnuty ve výsledku seskupené.</span><span class="sxs-lookup"><span data-stu-id="264f2-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="264f2-111">Pokud nebyla určena žádná pole, všechna pole, proměnná dotazu nebo proměnné jsou zahrnuty ve výsledku seskupené.</span><span class="sxs-lookup"><span data-stu-id="264f2-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="264f2-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="264f2-112">Required.</span></span> <span data-ttu-id="264f2-113">Výraz, který určuje klíč pro použití k určení skupiny prvků.</span><span class="sxs-lookup"><span data-stu-id="264f2-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="264f2-114">Můžete zadat více než jeden klíč k určení složený klíč.</span><span class="sxs-lookup"><span data-stu-id="264f2-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="264f2-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="264f2-115">Optional.</span></span> <span data-ttu-id="264f2-116">Jeden nebo více dalších klíčů, které jsou spojené s `keyExp1` vytvoření složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="264f2-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="264f2-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="264f2-117">Required.</span></span> <span data-ttu-id="264f2-118">Jeden nebo více výrazů, které určují, jak se agregují skupiny.</span><span class="sxs-lookup"><span data-stu-id="264f2-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="264f2-119">Chcete-li zjistit název člena pro seskupené výsledky, použijte `Group` – klíčové slovo, které může být v některém z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="264f2-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="264f2-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="264f2-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="264f2-121">Může také obsahovat agregační funkce, které chcete aplikovat ve skupině.</span><span class="sxs-lookup"><span data-stu-id="264f2-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="264f2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="264f2-122">Remarks</span></span>  
 <span data-ttu-id="264f2-123">Můžete použít `Group By` klauzule přerušení výsledků dotazu do skupin.</span><span class="sxs-lookup"><span data-stu-id="264f2-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="264f2-124">Seskupení podle klíče nebo složený klíč skládající se z více klíčů.</span><span class="sxs-lookup"><span data-stu-id="264f2-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="264f2-125">Prvky, které jsou spojeny s odpovídající hodnoty klíče jsou součástí stejné skupiny.</span><span class="sxs-lookup"><span data-stu-id="264f2-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="264f2-126">Můžete použít `aggregateList` parametr `Into` klauzule a `Group` – klíčové slovo k identifikaci názvu členu, který se používá k odkazování skupiny.</span><span class="sxs-lookup"><span data-stu-id="264f2-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="264f2-127">Můžete použít také v agregačních funkcí `Into` klauzule k výpočtu hodnot seskupených elementů.</span><span class="sxs-lookup"><span data-stu-id="264f2-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="264f2-128">Seznam standardní agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="264f2-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="264f2-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="264f2-129">Example</span></span>  
 <span data-ttu-id="264f2-130">Následující příklad kódu seskupí seznam zákazníků na základě jejich umístění (země nebo oblast) a poskytuje počet zákazníků v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="264f2-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="264f2-131">Výsledky jsou seřazené podle názvu země/oblast.</span><span class="sxs-lookup"><span data-stu-id="264f2-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="264f2-132">Seskupené výsledky jsou řazeny podle název města.</span><span class="sxs-lookup"><span data-stu-id="264f2-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="264f2-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="264f2-133">See also</span></span>

- [<span data-ttu-id="264f2-134">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="264f2-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="264f2-135">Dotazy</span><span class="sxs-lookup"><span data-stu-id="264f2-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="264f2-136">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="264f2-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="264f2-137">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="264f2-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="264f2-138">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="264f2-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="264f2-139">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="264f2-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="264f2-140">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="264f2-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
