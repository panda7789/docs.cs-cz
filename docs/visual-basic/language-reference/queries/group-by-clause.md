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
ms.openlocfilehash: 5224c7b5ae1c8a83be07fdf5f2065794fb46dd55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625552"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="8482b-102">Group By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8482b-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="8482b-103">Seskupuje prvky sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8482b-103">Groups the elements of a query result.</span></span> <span data-ttu-id="8482b-104">Můžete také použít k aplikaci agregačních funkcí na každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="8482b-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="8482b-105">Operace seskupení je založená na jeden nebo více klíčů.</span><span class="sxs-lookup"><span data-stu-id="8482b-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8482b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8482b-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="8482b-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="8482b-107">Parts</span></span>  
  
- <span data-ttu-id="8482b-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="8482b-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="8482b-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="8482b-109">Optional.</span></span> <span data-ttu-id="8482b-110">Jedno nebo více polí proměnné dotazu nebo proměnné, které explicitně určete pole, které mají být zahrnuty ve výsledku seskupené.</span><span class="sxs-lookup"><span data-stu-id="8482b-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="8482b-111">Pokud nebyla určena žádná pole, všechna pole, proměnná dotazu nebo proměnné jsou zahrnuty ve výsledku seskupené.</span><span class="sxs-lookup"><span data-stu-id="8482b-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="8482b-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8482b-112">Required.</span></span> <span data-ttu-id="8482b-113">Výraz, který určuje klíč pro použití k určení skupiny prvků.</span><span class="sxs-lookup"><span data-stu-id="8482b-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="8482b-114">Můžete zadat více než jeden klíč k určení složený klíč.</span><span class="sxs-lookup"><span data-stu-id="8482b-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="8482b-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="8482b-115">Optional.</span></span> <span data-ttu-id="8482b-116">Jeden nebo více dalších klíčů, které jsou spojené s `keyExp1` vytvoření složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="8482b-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="8482b-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8482b-117">Required.</span></span> <span data-ttu-id="8482b-118">Jeden nebo více výrazů, které určují, jak se agregují skupiny.</span><span class="sxs-lookup"><span data-stu-id="8482b-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="8482b-119">Chcete-li zjistit název člena pro seskupené výsledky, použijte `Group` – klíčové slovo, které může být v některém z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="8482b-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="8482b-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="8482b-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="8482b-121">Může také obsahovat agregační funkce, které chcete aplikovat ve skupině.</span><span class="sxs-lookup"><span data-stu-id="8482b-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8482b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8482b-122">Remarks</span></span>  
 <span data-ttu-id="8482b-123">Můžete použít `Group By` klauzule přerušení výsledků dotazu do skupin.</span><span class="sxs-lookup"><span data-stu-id="8482b-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="8482b-124">Seskupení podle klíče nebo složený klíč skládající se z více klíčů.</span><span class="sxs-lookup"><span data-stu-id="8482b-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="8482b-125">Prvky, které jsou spojeny s odpovídající hodnoty klíče jsou součástí stejné skupiny.</span><span class="sxs-lookup"><span data-stu-id="8482b-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="8482b-126">Můžete použít `aggregateList` parametr `Into` klauzule a `Group` – klíčové slovo k identifikaci názvu členu, který se používá k odkazování skupiny.</span><span class="sxs-lookup"><span data-stu-id="8482b-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="8482b-127">Můžete použít také v agregačních funkcí `Into` klauzule k výpočtu hodnot seskupených elementů.</span><span class="sxs-lookup"><span data-stu-id="8482b-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="8482b-128">Seznam standardní agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8482b-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8482b-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="8482b-129">Example</span></span>  
 <span data-ttu-id="8482b-130">Následující příklad kódu seskupí seznam zákazníků na základě jejich umístění (a případně zemi) a poskytuje počet zákazníků v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="8482b-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="8482b-131">Výsledky jsou seřazené podle názvu země.</span><span class="sxs-lookup"><span data-stu-id="8482b-131">The results are ordered by country name.</span></span> <span data-ttu-id="8482b-132">Seskupené výsledky jsou řazeny podle název města.</span><span class="sxs-lookup"><span data-stu-id="8482b-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="8482b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8482b-133">See also</span></span>

- [<span data-ttu-id="8482b-134">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8482b-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="8482b-135">Dotazy</span><span class="sxs-lookup"><span data-stu-id="8482b-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="8482b-136">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="8482b-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="8482b-137">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="8482b-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="8482b-138">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="8482b-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="8482b-139">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="8482b-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="8482b-140">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="8482b-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
