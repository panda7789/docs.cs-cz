---
title: Dynamicky určovat predikátové filtry za běhu (LINQ v C#)
description: Zjistěte, jak dynamicky určit predikátové filtry za běhu pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659940"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="d9331-103">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="d9331-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="d9331-104">V některých případech nevíte až do běhu, kolik predikáty musíte použít `where` na zdrojové prvky v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d9331-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="d9331-105">Jedním ze způsobů, jak dynamicky určit více <xref:System.Linq.Enumerable.Contains%2A> predikátových filtrů, je použití metody, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d9331-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="d9331-106">Příklad je konstruován dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="d9331-106">The example is constructed in two ways.</span></span> <span data-ttu-id="d9331-107">Nejprve je projekt spuštěn filtrováním hodnot, které jsou k dispozici v programu.</span><span class="sxs-lookup"><span data-stu-id="d9331-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="d9331-108">Potom je projekt spuštěn znovu pomocí vstupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="d9331-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="d9331-109">Filtrování pomocí metody Contains</span><span class="sxs-lookup"><span data-stu-id="d9331-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="d9331-110">Otevřete novou konzolovou `PredicateFilters`aplikaci a pojmenujte ji .</span><span class="sxs-lookup"><span data-stu-id="d9331-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="d9331-111">Zkopírujte `StudentClass` třídu z [query kolekce objektů](query-a-collection-of-objects.md) a `PredicateFilters` vložte ji do oboru názvů pod třídou `Program`.</span><span class="sxs-lookup"><span data-stu-id="d9331-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="d9331-112">`StudentClass`obsahuje seznam `Student` objektů.</span><span class="sxs-lookup"><span data-stu-id="d9331-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="d9331-113">Zakomentujte `Main` `StudentClass`metodu v .</span><span class="sxs-lookup"><span data-stu-id="d9331-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="d9331-114">Nahraďte třídu `Program` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d9331-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="d9331-115">Přidejte následující řádek `Main` k `DynamicPredicates`metodě ve `ids`třídě pod deklarací .</span><span class="sxs-lookup"><span data-stu-id="d9331-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="d9331-116">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="d9331-116">Run the project.</span></span>

7. <span data-ttu-id="d9331-117">V okně konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d9331-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="d9331-118">Garciová: 114</span><span class="sxs-lookup"><span data-stu-id="d9331-118">Garcia: 114</span></span>

     <span data-ttu-id="d9331-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="d9331-119">O'Donnell: 112</span></span>

     <span data-ttu-id="d9331-120">Omelčenková: 111</span><span class="sxs-lookup"><span data-stu-id="d9331-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="d9331-121">Dalším krokem je spuštění projektu znovu, tentokrát pomocí vstupu zadaného `ids`za běhu namísto pole .</span><span class="sxs-lookup"><span data-stu-id="d9331-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="d9331-122">Změnit `QueryByID(ids)` `QueryByID(args)` na `Main` v metodě.</span><span class="sxs-lookup"><span data-stu-id="d9331-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="d9331-123">Spusťte projekt s argumenty `122 117 120 115`příkazového řádku .</span><span class="sxs-lookup"><span data-stu-id="d9331-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="d9331-124">Při spuštění projektu se tyto hodnoty `args`stanou prvky `Main` , parametrmetody.</span><span class="sxs-lookup"><span data-stu-id="d9331-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method.</span></span>

10. <span data-ttu-id="d9331-125">V okně konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d9331-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="d9331-126">Adamsová: 120</span><span class="sxs-lookup"><span data-stu-id="d9331-126">Adams: 120</span></span>

     <span data-ttu-id="d9331-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="d9331-127">Feng: 117</span></span>

     <span data-ttu-id="d9331-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="d9331-128">Garcia: 115</span></span>

     <span data-ttu-id="d9331-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="d9331-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="d9331-130">Filtrování pomocí příkazu switch</span><span class="sxs-lookup"><span data-stu-id="d9331-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="d9331-131">Příkaz můžete `switch` použít k výběru mezi předem určenými alternativními dotazy.</span><span class="sxs-lookup"><span data-stu-id="d9331-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="d9331-132">V následujícím příkladu `studentQuery` používá `where` jinou klauzuli v závislosti na úrovni stupně nebo rok, je určen za běhu.</span><span class="sxs-lookup"><span data-stu-id="d9331-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="d9331-133">Zkopírujte následující metodu a `DynamicPredicates`vložte ji do třídy .</span><span class="sxs-lookup"><span data-stu-id="d9331-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="d9331-134">V `Main` metodě nahraďte `QueryByID` volání následujícím voláním, které odešle první prvek z `args` pole jako svůj argument: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="d9331-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="d9331-135">Spusťte projekt s argumentem příkazového řádku s hodnotou celéčíslo mezi 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="d9331-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9331-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9331-136">See also</span></span>

- [<span data-ttu-id="d9331-137">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="d9331-137">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="d9331-138">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="d9331-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
