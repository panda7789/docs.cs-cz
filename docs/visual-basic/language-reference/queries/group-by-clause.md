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
ms.openlocfilehash: 8b3a480c226debc529c268e83437d15192592bd3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004751"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="ce26d-102">Group By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce26d-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="ce26d-103">Seskupí prvky výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ce26d-103">Groups the elements of a query result.</span></span> <span data-ttu-id="ce26d-104">Lze také použít k aplikování agregačních funkcí na každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="ce26d-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="ce26d-105">Operace seskupení je založena na jednom nebo více klíčích.</span><span class="sxs-lookup"><span data-stu-id="ce26d-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce26d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce26d-106">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="ce26d-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="ce26d-107">Parts</span></span>  
  
- <span data-ttu-id="ce26d-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="ce26d-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="ce26d-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ce26d-109">Optional.</span></span> <span data-ttu-id="ce26d-110">Jedno nebo více polí proměnné nebo proměnných dotazu, které explicitně identifikují pole, která mají být součástí seskupeného výsledku.</span><span class="sxs-lookup"><span data-stu-id="ce26d-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="ce26d-111">Nejsou-li zadána žádná pole, jsou v seskupeném výsledku obsažena všechna pole proměnné dotazu nebo proměnné.</span><span class="sxs-lookup"><span data-stu-id="ce26d-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="ce26d-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ce26d-112">Required.</span></span> <span data-ttu-id="ce26d-113">Výraz, který identifikuje klíč, který se má použít k určení skupin prvků.</span><span class="sxs-lookup"><span data-stu-id="ce26d-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="ce26d-114">Můžete zadat více než jeden klíč, který určí složený klíč.</span><span class="sxs-lookup"><span data-stu-id="ce26d-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="ce26d-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ce26d-115">Optional.</span></span> <span data-ttu-id="ce26d-116">Jeden nebo více dalších klíčů, které jsou kombinovány s `keyExp1` pro vytvoření složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="ce26d-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="ce26d-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ce26d-117">Required.</span></span> <span data-ttu-id="ce26d-118">Jeden nebo více výrazů, které identifikují způsob agregace skupin.</span><span class="sxs-lookup"><span data-stu-id="ce26d-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="ce26d-119">Chcete-li identifikovat název člena pro seskupené výsledky, použijte klíčové slovo `Group`, které může být v jednom z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="ce26d-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="ce26d-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="ce26d-120">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="ce26d-121">Můžete také zahrnout agregační funkce, které se mají použít pro skupinu.</span><span class="sxs-lookup"><span data-stu-id="ce26d-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce26d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce26d-122">Remarks</span></span>  
 <span data-ttu-id="ce26d-123">K přerušení výsledků dotazu do skupin lze použít klauzuli `Group By`.</span><span class="sxs-lookup"><span data-stu-id="ce26d-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="ce26d-124">Seskupení je založeno na klíči nebo složeném klíči, který se skládá z více klíčů.</span><span class="sxs-lookup"><span data-stu-id="ce26d-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="ce26d-125">Prvky, které jsou přidruženy k odpovídajícím hodnotám klíčů, jsou zahrnuty ve stejné skupině.</span><span class="sxs-lookup"><span data-stu-id="ce26d-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="ce26d-126">Použijete parametr `aggregateList` klauzule `Into` a klíčové slovo `Group` k identifikaci názvu člena, který se používá k odkazování na skupinu.</span><span class="sxs-lookup"><span data-stu-id="ce26d-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="ce26d-127">V klauzuli `Into` můžete také zahrnout agregační funkce pro výpočet hodnot seskupených prvků.</span><span class="sxs-lookup"><span data-stu-id="ce26d-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="ce26d-128">Seznam standardních agregačních funkcí naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ce26d-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce26d-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce26d-129">Example</span></span>  
 <span data-ttu-id="ce26d-130">Následující příklad kódu seskupuje seznam zákazníků na základě jejich umístění (země/oblast) a poskytuje počet zákazníků v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="ce26d-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="ce26d-131">Výsledky jsou seřazené podle názvu země nebo oblasti.</span><span class="sxs-lookup"><span data-stu-id="ce26d-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="ce26d-132">Seskupené výsledky jsou seřazené podle názvu města.</span><span class="sxs-lookup"><span data-stu-id="ce26d-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ce26d-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce26d-133">See also</span></span>

- [<span data-ttu-id="ce26d-134">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce26d-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ce26d-135">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ce26d-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ce26d-136">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="ce26d-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ce26d-137">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="ce26d-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ce26d-138">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="ce26d-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="ce26d-139">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="ce26d-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ce26d-140">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="ce26d-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
