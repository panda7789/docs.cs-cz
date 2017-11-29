---
title: "Dynamické určování filtrů predikátů při běhu"
description: "Jak dynamické určování filtrů predikátů při běhu."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 06bc594ac1357e7dca6c182fa28310559a79875c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="67454-104">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="67454-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="67454-105">V některých případech si nejste jisti, dokud běhu musíte použít zdrojové elementy v tom, kolik predikáty `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="67454-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="67454-106">Dynamické určování filtrů několik predikátů jedním ze způsobů je používat <xref:System.Linq.Enumerable.Contains%2A> metoda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="67454-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="67454-107">V příkladu je vytvořen dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="67454-107">The example is constructed in two ways.</span></span> <span data-ttu-id="67454-108">Nejprve spustit projekt na filtrování na hodnotách, které jsou součástí programu.</span><span class="sxs-lookup"><span data-stu-id="67454-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="67454-109">Projekt je pak spusťte znovu pomocí vstup za běhu.</span><span class="sxs-lookup"><span data-stu-id="67454-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="67454-110">Chcete-li filtrovat pomocí metody obsahuje</span><span class="sxs-lookup"><span data-stu-id="67454-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="67454-111">Otevřete novou konzolovou aplikaci a pojmenujte ji `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="67454-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="67454-112">Kopírování `StudentClass` třídy z [dotazování na kolekci objektů](query-a-collection-of-objects.md) a vložte jej do oboru názvů `PredicateFilters` pod Třída `Program`.</span><span class="sxs-lookup"><span data-stu-id="67454-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="67454-113">`StudentClass`obsahuje seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="67454-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="67454-114">Komentář `Main` metoda v `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="67454-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="67454-115">Změňte třídu `Program` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="67454-115">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="67454-116">Přidejte následující řádek na `Main` metodu v třídě `DynamicPredicates`, v části prohlášení o `ids`.</span><span class="sxs-lookup"><span data-stu-id="67454-116">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="67454-117">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="67454-117">Run the project.</span></span>  
  
7.  <span data-ttu-id="67454-118">V okně konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="67454-118">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="67454-119">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="67454-119">Garcia: 114</span></span>  
  
     <span data-ttu-id="67454-120">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="67454-120">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="67454-121">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="67454-121">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="67454-122">Dalším krokem je spusťte projekt znovu, tentokrát pomocí vstup zadaný v době běhu místo pole `ids`.</span><span class="sxs-lookup"><span data-stu-id="67454-122">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="67454-123">Změna `QueryByID(ids)` k `QueryByID(args)` v `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="67454-123">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="67454-124">Spusťte projekt s argumenty příkazového řádku `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="67454-124">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="67454-125">Při spuštění projektu tyto hodnoty stát prvky `args`, parametr `Main` metoda...</span><span class="sxs-lookup"><span data-stu-id="67454-125">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="67454-126">V okně konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="67454-126">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="67454-127">Adams: 120.</span><span class="sxs-lookup"><span data-stu-id="67454-127">Adams: 120</span></span>  
  
     <span data-ttu-id="67454-128">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="67454-128">Feng: 117</span></span>  
  
     <span data-ttu-id="67454-129">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="67454-129">Garcia: 115</span></span>  
  
     <span data-ttu-id="67454-130">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="67454-130">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="67454-131">Chcete-li filtrovat pomocí příkazu switch</span><span class="sxs-lookup"><span data-stu-id="67454-131">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="67454-132">Můžete použít `switch` příkaz chcete vybrat z předem určeny alternativní dotazy.</span><span class="sxs-lookup"><span data-stu-id="67454-132">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="67454-133">V následujícím příkladu `studentQuery` používá jiné `where` klauzule v závislosti na tom, které úrovni úroveň nebo rok, je zadána v době běhu.</span><span class="sxs-lookup"><span data-stu-id="67454-133">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="67454-134">Zkopírujte následující metodu a vložte ho do třídy `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="67454-134">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="67454-135">V `Main` metoda, nahraďte volání `QueryByID` s následující volání, která odešle první prvek z `args` pole jako její argument: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="67454-135">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="67454-136">Spusťte projekt s argumentem příkazového řádku ve celočíselnou hodnotu mezi 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="67454-136">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="67454-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="67454-137">See Also</span></span>  
 [<span data-ttu-id="67454-138">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="67454-138">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="67454-139">kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="67454-139">where clause</span></span>](../language-reference/keywords/where-clause.md)
