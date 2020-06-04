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
ms.openlocfilehash: 5fce4f818e22373de7f1b37b941fd88155f3a33f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359887"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="6a3d7-102">Group By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a3d7-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="6a3d7-103">Seskupí prvky výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-103">Groups the elements of a query result.</span></span> <span data-ttu-id="6a3d7-104">Lze také použít k aplikování agregačních funkcí na každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="6a3d7-105">Operace seskupení je založena na jednom nebo více klíčích.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a3d7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a3d7-106">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="6a3d7-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="6a3d7-107">Parts</span></span>  
  
- <span data-ttu-id="6a3d7-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="6a3d7-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="6a3d7-109">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-109">Optional.</span></span> <span data-ttu-id="6a3d7-110">Jedno nebo více polí proměnné nebo proměnných dotazu, které explicitně identifikují pole, která mají být součástí seskupeného výsledku.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="6a3d7-111">Nejsou-li zadána žádná pole, jsou v seskupeném výsledku obsažena všechna pole proměnné dotazu nebo proměnné.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="6a3d7-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-112">Required.</span></span> <span data-ttu-id="6a3d7-113">Výraz, který identifikuje klíč, který se má použít k určení skupin prvků.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="6a3d7-114">Můžete zadat více než jeden klíč, který určí složený klíč.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="6a3d7-115">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-115">Optional.</span></span> <span data-ttu-id="6a3d7-116">Jeden nebo více dalších klíčů, které jsou kombinovány s nástrojem `keyExp1` k vytvoření složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="6a3d7-117">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-117">Required.</span></span> <span data-ttu-id="6a3d7-118">Jeden nebo více výrazů, které identifikují způsob agregace skupin.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="6a3d7-119">Chcete-li identifikovat název člena pro seskupené výsledky, použijte `Group` klíčové slovo, které může být v jednom z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="6a3d7-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="6a3d7-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6a3d7-120">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="6a3d7-121">Můžete také zahrnout agregační funkce, které se mají použít pro skupinu.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a3d7-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a3d7-122">Remarks</span></span>  
 <span data-ttu-id="6a3d7-123">Klauzuli můžete použít `Group By` k přerušení výsledků dotazu do skupin.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="6a3d7-124">Seskupení je založeno na klíči nebo složeném klíči, který se skládá z více klíčů.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="6a3d7-125">Prvky, které jsou přidruženy k odpovídajícím hodnotám klíčů, jsou zahrnuty ve stejné skupině.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="6a3d7-126">Použijete `aggregateList` parametr `Into` klauzule a `Group` klíčové slovo k identifikaci názvu člena, který se používá k odkazování na skupinu.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="6a3d7-127">Můžete také zahrnout agregační funkce v `Into` klauzuli pro výpočet hodnot pro seskupené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="6a3d7-128">Seznam standardních agregačních funkcí naleznete v tématu [klauzule Aggregate](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6a3d7-128">For a list of standard aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a3d7-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a3d7-129">Example</span></span>  
 <span data-ttu-id="6a3d7-130">Následující příklad kódu seskupuje seznam zákazníků na základě jejich umístění (země/oblast) a poskytuje počet zákazníků v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="6a3d7-131">Výsledky jsou seřazené podle názvu země nebo oblasti.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="6a3d7-132">Seskupené výsledky jsou seřazené podle názvu města.</span><span class="sxs-lookup"><span data-stu-id="6a3d7-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="6a3d7-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a3d7-133">See also</span></span>

- [<span data-ttu-id="6a3d7-134">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a3d7-134">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6a3d7-135">Dotazy</span><span class="sxs-lookup"><span data-stu-id="6a3d7-135">Queries</span></span>](index.md)
- [<span data-ttu-id="6a3d7-136">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="6a3d7-136">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="6a3d7-137">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="6a3d7-137">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="6a3d7-138">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="6a3d7-138">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="6a3d7-139">Aggregate – klauzule</span><span class="sxs-lookup"><span data-stu-id="6a3d7-139">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="6a3d7-140">Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="6a3d7-140">Group Join Clause</span></span>](group-join-clause.md)
