---
title: Rozměry pole
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 12e983ae62fa9f9ea762d434ffe5b73873a4a2e8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351898"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="acc14-102">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acc14-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="acc14-103">*Dimenze* je směr, ve kterém můžete měnit specifikaci prvků pole.</span><span class="sxs-lookup"><span data-stu-id="acc14-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="acc14-104">Pole, které obsahuje celkový prodej za každý den v měsíci, má jednu dimenzi (den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="acc14-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="acc14-105">Pole, které obsahuje celkové tržby podle oddělení za každý den v měsíci, má dvě dimenze (číslo oddělení a den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="acc14-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="acc14-106">Počet rozměrů, které pole je označováno jako *pořadí*.</span><span class="sxs-lookup"><span data-stu-id="acc14-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="acc14-107">Vlastnost <xref:System.Array.Rank%2A> lze použít k určení, kolik rozměrů pole má.</span><span class="sxs-lookup"><span data-stu-id="acc14-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="acc14-108">Práce s rozměry</span><span class="sxs-lookup"><span data-stu-id="acc14-108">Working with Dimensions</span></span>

<span data-ttu-id="acc14-109">Prvek pole určíte tak, že pro každou z jeho rozměrů zadáte *index* nebo *dolní index* .</span><span class="sxs-lookup"><span data-stu-id="acc14-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="acc14-110">Prvky jsou souvislé podél každé dimenze z indexu 0 až po nejvyšší index pro tuto dimenzi.</span><span class="sxs-lookup"><span data-stu-id="acc14-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="acc14-111">Následující ilustrace znázorňují koncepční strukturu polí s odlišným pořadím.</span><span class="sxs-lookup"><span data-stu-id="acc14-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="acc14-112">Každý prvek na ilustraci zobrazuje indexové hodnoty, které k němu přistupují.</span><span class="sxs-lookup"><span data-stu-id="acc14-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="acc14-113">Můžete například získat přístup k prvnímu prvku druhého řádku dvojrozměrného pole zadáním indexů `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="acc14-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Diagram, který zobrazuje jednorozměrné pole.](./media/array-dimensions/one-dimensional-array.gif)

![Diagram, který zobrazuje dvourozměrné pole.](./media/array-dimensions/two-dimensional-array.gif)

![Diagram, který zobrazuje trojrozměrné pole.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="acc14-117">Jedna dimenze</span><span class="sxs-lookup"><span data-stu-id="acc14-117">One Dimension</span></span>

<span data-ttu-id="acc14-118">Mnoho polí má pouze jednu dimenzi, například počet lidí každého stáří.</span><span class="sxs-lookup"><span data-stu-id="acc14-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="acc14-119">Jediným požadavkem určení prvku je stáří, pro které tento prvek obsahuje počet.</span><span class="sxs-lookup"><span data-stu-id="acc14-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="acc14-120">Proto takové pole používá pouze jeden index.</span><span class="sxs-lookup"><span data-stu-id="acc14-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="acc14-121">Následující příklad deklaruje proměnnou tak, aby obsahovala jednorozměrné *pole* počtů stáří pro věkové číslo 0 až 120.</span><span class="sxs-lookup"><span data-stu-id="acc14-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="acc14-122">Dvě dimenze</span><span class="sxs-lookup"><span data-stu-id="acc14-122">Two Dimensions</span></span>

<span data-ttu-id="acc14-123">Některá pole mají dvě dimenze, jako je třeba počet poboček na každém patře každé budovy na areálu.</span><span class="sxs-lookup"><span data-stu-id="acc14-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="acc14-124">Specifikace elementu vyžaduje stavební číslo i podlahu a každý prvek obsahuje počet pro tuto kombinaci sestavování a podlaží.</span><span class="sxs-lookup"><span data-stu-id="acc14-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="acc14-125">Proto takové pole používá dva indexy.</span><span class="sxs-lookup"><span data-stu-id="acc14-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="acc14-126">Následující příklad deklaruje proměnnou pro uchování *dvojrozměrného pole* počtů kanceláří pro budovy 0 až 40 a podlah 0 až 5.</span><span class="sxs-lookup"><span data-stu-id="acc14-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="acc14-127">Dvourozměrné pole se označuje také jako *obdélníkové pole*.</span><span class="sxs-lookup"><span data-stu-id="acc14-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="acc14-128">Tři rozměry</span><span class="sxs-lookup"><span data-stu-id="acc14-128">Three Dimensions</span></span>

<span data-ttu-id="acc14-129">Několik polí má tři dimenze, například hodnoty v trojrozměrném prostoru.</span><span class="sxs-lookup"><span data-stu-id="acc14-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="acc14-130">Takové pole používá tři indexy, což v tomto případě představuje souřadnice x, y a z fyzického místa.</span><span class="sxs-lookup"><span data-stu-id="acc14-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="acc14-131">Následující příklad deklaruje proměnnou pro uchování *trojrozměrného pole* teploty vzduchu v různých místech trojrozměrného svazku.</span><span class="sxs-lookup"><span data-stu-id="acc14-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="acc14-132">Více než tři dimenze</span><span class="sxs-lookup"><span data-stu-id="acc14-132">More than Three Dimensions</span></span>

<span data-ttu-id="acc14-133">I když pole může mít až 32 dimenzí, je zřídka více než tři.</span><span class="sxs-lookup"><span data-stu-id="acc14-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="acc14-134">Když přidáte dimenze do pole, celkové úložiště, které je potřeba pro pole, se výrazně zvětšuje, takže používejte multidimenzionální pole s rozvahou.</span><span class="sxs-lookup"><span data-stu-id="acc14-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="acc14-135">Používání různých dimenzí</span><span class="sxs-lookup"><span data-stu-id="acc14-135">Using Different Dimensions</span></span>

<span data-ttu-id="acc14-136">Předpokládejme, že chcete sledovat tržby za každý den v daném měsíci.</span><span class="sxs-lookup"><span data-stu-id="acc14-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="acc14-137">Je možné deklarovat jednorozměrné pole s 31 prvky, jeden pro každý den v měsíci, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="acc14-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="acc14-138">Nyní předpokládejme, že chcete sledovat stejné informace nejen pro každý den v měsíci, ale také pro každý měsíc v roce.</span><span class="sxs-lookup"><span data-stu-id="acc14-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="acc14-139">Můžete deklarovat dvojrozměrné pole s 12 řádky (za měsíc) a 31 sloupců (pro dny), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="acc14-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="acc14-140">Nyní se můžete rozhodnout, že budete mít informace o poznámkovém poli po dobu více než jednoho roku.</span><span class="sxs-lookup"><span data-stu-id="acc14-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="acc14-141">Pokud chcete sledovat prodejní objemy po dobu 5 let, můžete deklarovat trojrozměrné pole s 5 vrstvami, 12 řádky a 31 sloupci, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="acc14-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="acc14-142">Všimněte si, že vzhledem k tomu, že se každý index mění z 0 na jeho maximum, každá dimenze `salesAmounts` je deklarována jako méně než požadovaná délka pro tuto dimenzi.</span><span class="sxs-lookup"><span data-stu-id="acc14-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="acc14-143">Všimněte si také, že velikost pole se zvyšuje s každou novou dimenzí.</span><span class="sxs-lookup"><span data-stu-id="acc14-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="acc14-144">Tři velikosti v předchozích příkladech jsou 31, 372 a 1 860 prvky.</span><span class="sxs-lookup"><span data-stu-id="acc14-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="acc14-145">Pole lze vytvořit bez použití příkazu `Dim` nebo klauzule `New`.</span><span class="sxs-lookup"><span data-stu-id="acc14-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="acc14-146">Například můžete zavolat metodu <xref:System.Array.CreateInstance%2A>, nebo jiná komponenta může předat vašemu kódu pole vytvořené tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="acc14-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="acc14-147">Takové pole může mít dolní mez, která je jiná než 0.</span><span class="sxs-lookup"><span data-stu-id="acc14-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="acc14-148">Můžete vždy testovat spodní mez dimenze pomocí metody <xref:System.Array.GetLowerBound%2A> nebo funkce `LBound`.</span><span class="sxs-lookup"><span data-stu-id="acc14-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="acc14-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acc14-149">See also</span></span>

- [<span data-ttu-id="acc14-150">Pole</span><span class="sxs-lookup"><span data-stu-id="acc14-150">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="acc14-151">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="acc14-151">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
