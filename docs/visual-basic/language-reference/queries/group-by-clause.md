---
title: "Group By – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="e6c03-102">Group By – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6c03-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="e6c03-103">Skupiny elementy výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6c03-103">Groups the elements of a query result.</span></span> <span data-ttu-id="e6c03-104">Můžete také použít k použití agregační funkce pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="e6c03-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="e6c03-105">Operace seskupení je založena na jeden nebo více klíčů.</span><span class="sxs-lookup"><span data-stu-id="e6c03-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c03-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6c03-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="e6c03-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="e6c03-107">Parts</span></span>  
  
-   <span data-ttu-id="e6c03-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="e6c03-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="e6c03-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e6c03-109">Optional.</span></span> <span data-ttu-id="e6c03-110">Jeden nebo více polí proměnné dotazu nebo proměnné, které explicitně určit pole, která má být zahrnut v seskupené výsledek.</span><span class="sxs-lookup"><span data-stu-id="e6c03-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="e6c03-111">Pokud nejsou zadaná žádná pole, všechna pole dotazu proměnné nebo proměnné jsou součástí seskupené výsledek.</span><span class="sxs-lookup"><span data-stu-id="e6c03-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="e6c03-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e6c03-112">Required.</span></span> <span data-ttu-id="e6c03-113">Výraz, který identifikuje klíč sloužící k určení skupiny elementů.</span><span class="sxs-lookup"><span data-stu-id="e6c03-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="e6c03-114">Můžete zadat více než jeden klíč k určení složený klíč.</span><span class="sxs-lookup"><span data-stu-id="e6c03-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="e6c03-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e6c03-115">Optional.</span></span> <span data-ttu-id="e6c03-116">Jeden nebo více dalších klíčů, které jsou spojené s `keyExp1` k vytvoření složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="e6c03-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="e6c03-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e6c03-117">Required.</span></span> <span data-ttu-id="e6c03-118">Jeden nebo více výrazů, které určují, jak jsou agregovat do skupin.</span><span class="sxs-lookup"><span data-stu-id="e6c03-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="e6c03-119">Lze zjistit název člena seskupené výsledků `Group` – klíčové slovo, které může být v některém z následujících podob:</span><span class="sxs-lookup"><span data-stu-id="e6c03-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="e6c03-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e6c03-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="e6c03-121">Můžete použít také agregační funkce na aplikujete na skupinu.</span><span class="sxs-lookup"><span data-stu-id="e6c03-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6c03-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6c03-122">Remarks</span></span>  
 <span data-ttu-id="e6c03-123">Můžete použít `Group By` klauzule rozdělte výsledků dotazu do skupin.</span><span class="sxs-lookup"><span data-stu-id="e6c03-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="e6c03-124">Seskupení podle klíče nebo složený klíč, který se skládá z více klíčů.</span><span class="sxs-lookup"><span data-stu-id="e6c03-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="e6c03-125">Elementy, které jsou spojeny s odpovídajícím hodnoty klíče jsou součástí stejné skupiny.</span><span class="sxs-lookup"><span data-stu-id="e6c03-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="e6c03-126">Můžete použít `aggregateList` parametr `Into` klauzule a `Group` – klíčové slovo k identifikaci název člena, který slouží k odkazování skupině.</span><span class="sxs-lookup"><span data-stu-id="e6c03-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="e6c03-127">Můžete použít také agregačních funkcí ve `Into` klauzule k výpočtu hodnoty pro seskupené elementy.</span><span class="sxs-lookup"><span data-stu-id="e6c03-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="e6c03-128">Seznam standardní agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6c03-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c03-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6c03-129">Example</span></span>  
 <span data-ttu-id="e6c03-130">Následující příklad kódu skupiny seznamu odběratelů založené na jejich umístění (země) a poskytuje počet zákazníků v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="e6c03-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="e6c03-131">Výsledky jsou seřazené podle názvu země.</span><span class="sxs-lookup"><span data-stu-id="e6c03-131">The results are ordered by country name.</span></span> <span data-ttu-id="e6c03-132">Seskupené výsledky jsou seřazené podle název města.</span><span class="sxs-lookup"><span data-stu-id="e6c03-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e6c03-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6c03-133">See Also</span></span>  
 [<span data-ttu-id="e6c03-134">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6c03-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="e6c03-135">Dotazy</span><span class="sxs-lookup"><span data-stu-id="e6c03-135">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="e6c03-136">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6c03-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="e6c03-137">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6c03-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="e6c03-138">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6c03-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="e6c03-139">AGGREGATE – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6c03-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="e6c03-140">Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6c03-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
