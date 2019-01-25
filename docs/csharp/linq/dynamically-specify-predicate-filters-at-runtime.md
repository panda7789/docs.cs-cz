---
title: Dynamické určování filtrů predikátů při běhu (LINQ v JAZYKU C#)
description: Zjistěte, jak dynamické určování filtrů predikátů při běhu pomocí jazyka LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857733"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="01632-103">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="01632-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="01632-104">V některých případech neznáte až do běhu je nutné použít na zdrojové prvky v tom, kolik predikáty `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="01632-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="01632-105">Dynamické určování filtrů více predikátů jedním ze způsobů je použít <xref:System.Linq.Enumerable.Contains%2A> způsob, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="01632-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="01632-106">V příkladu je vytvořen dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="01632-106">The example is constructed in two ways.</span></span> <span data-ttu-id="01632-107">Projekt je nejprve spusťte pomocí filtrování podle hodnoty, které jsou k dispozici v programu.</span><span class="sxs-lookup"><span data-stu-id="01632-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="01632-108">Potom projekt spusťte znovu s použitím vstup v době běhu.</span><span class="sxs-lookup"><span data-stu-id="01632-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="01632-109">Chcete-li filtrovat pomocí metody obsahuje</span><span class="sxs-lookup"><span data-stu-id="01632-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="01632-110">Otevřete novou konzolovou aplikaci a pojmenujte ho `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="01632-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="01632-111">Kopírovat `StudentClass` třídy z [dotazování na kolekci objektů](query-a-collection-of-objects.md) a vložte ho do oboru názvů `PredicateFilters` pod třídy `Program`.</span><span class="sxs-lookup"><span data-stu-id="01632-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="01632-112">`StudentClass` obsahuje seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="01632-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="01632-113">Okomentujte `Main` metoda ve `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="01632-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="01632-114">Změňte třídu `Program` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="01632-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="01632-115">Přidejte následující řádek, který `Main` metody ve třídě `DynamicPredicates`, v části prohlášení o `ids`.</span><span class="sxs-lookup"><span data-stu-id="01632-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="01632-116">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="01632-116">Run the project.</span></span>

7. <span data-ttu-id="01632-117">V okně konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="01632-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="01632-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="01632-118">Garcia: 114</span></span>

     <span data-ttu-id="01632-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="01632-119">O'Donnell: 112</span></span>

     <span data-ttu-id="01632-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="01632-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="01632-121">Dalším krokem je spusťte projekt znovu, tentokrát pomocí vstup zadaný v době běhu místo pole `ids`.</span><span class="sxs-lookup"><span data-stu-id="01632-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="01632-122">Změna `QueryByID(ids)` k `QueryByID(args)` v `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="01632-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="01632-123">Spustit projekt s argumenty příkazového řádku `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="01632-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="01632-124">Při spuštění projektu, budou tyto hodnoty prvků `args`, parametr `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="01632-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method.</span></span>

10. <span data-ttu-id="01632-125">V okně konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="01632-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="01632-126">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="01632-126">Adams: 120</span></span>

     <span data-ttu-id="01632-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="01632-127">Feng: 117</span></span>

     <span data-ttu-id="01632-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="01632-128">Garcia: 115</span></span>

     <span data-ttu-id="01632-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="01632-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="01632-130">Chcete-li filtrovat pomocí příkazu switch</span><span class="sxs-lookup"><span data-stu-id="01632-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="01632-131">Můžete použít `switch` příkaz k výběru mezi předdefinovány alternativní dotazy.</span><span class="sxs-lookup"><span data-stu-id="01632-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="01632-132">V následujícím příkladu `studentQuery` používá jiný `where` klauzule v závislosti na tom, které na podnikové úrovni je zadána úroveň nebo rok v době běhu.</span><span class="sxs-lookup"><span data-stu-id="01632-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="01632-133">Následující metodu zkopírujte a vložte jej do třídy `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="01632-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="01632-134">V `Main` metoda, nahraďte volání `QueryByID` s následující volání, která odešle první prvek z `args` pole jako svůj argument: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="01632-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="01632-135">Spusťte projekt s argumentem příkazového řádku celočíselnou hodnotu mezi 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="01632-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="01632-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01632-136">See also</span></span>

- [<span data-ttu-id="01632-137">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="01632-137">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="01632-138">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="01632-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
