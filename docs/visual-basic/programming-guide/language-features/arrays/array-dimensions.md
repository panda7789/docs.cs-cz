---
title: Rozměry pole v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053714"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="136fb-102">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="136fb-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="136fb-103">A *dimenze* je směr, ve kterém můžete měnit specifikace prvků tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="136fb-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="136fb-104">Pole, která obsahuje celkový prodej za každý den v měsíci má jednu dimenzi (den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="136fb-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="136fb-105">Pole, která obsahuje celkový prodej podle oddělení pro každý den v měsíci má dvě dimenze (číslo oddělení a den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="136fb-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="136fb-106">Počet rozměrů pole má nazývá jeho *pořadí*.</span><span class="sxs-lookup"><span data-stu-id="136fb-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="136fb-107">Můžete použít <xref:System.Array.Rank%2A> vlastnosti k určení, kolik rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="136fb-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="136fb-108">Práce s rozměry</span><span class="sxs-lookup"><span data-stu-id="136fb-108">Working with Dimensions</span></span>  
 <span data-ttu-id="136fb-109">Určit element pole zadáním *index* nebo *dolní index* pro každé své dimenze.</span><span class="sxs-lookup"><span data-stu-id="136fb-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="136fb-110">Prvky jsou souvislé podél každé dimenze od indexu 0 až po nejvyšší index pro tuto dimenzi.</span><span class="sxs-lookup"><span data-stu-id="136fb-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="136fb-111">Na následujících obrázcích je koncepční struktura polí se různé rozměry.</span><span class="sxs-lookup"><span data-stu-id="136fb-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="136fb-112">Každý prvek na obrázcích zobrazuje hodnoty indexu, které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="136fb-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="136fb-113">Například můžete přístup k první prvek druhého řádku dvourozměrné pole tak, že zadáte indexy `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="136fb-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 ![Diagram zobrazující průběh jednorozměrné pole.](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![Diagram zobrazující průběh dvourozměrné pole.](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![Diagram zobrazující průběh trojrozměrného pole.](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a><span data-ttu-id="136fb-117">Jedna dimenze</span><span class="sxs-lookup"><span data-stu-id="136fb-117">One Dimension</span></span>  
 <span data-ttu-id="136fb-118">Mnoho pole mají pouze jednu dimenzi, například počet lidí každý věk.</span><span class="sxs-lookup"><span data-stu-id="136fb-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="136fb-119">Chcete-li určit element Jediným požadavkem je věk, pro které tento prvek obsahuje počet.</span><span class="sxs-lookup"><span data-stu-id="136fb-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="136fb-120">Proto se takové pole používá pouze jeden index.</span><span class="sxs-lookup"><span data-stu-id="136fb-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="136fb-121">Následující příklad deklaruje proměnnou pro uchování *jednorozměrné pole* věku se počítá od 0 až 120.</span><span class="sxs-lookup"><span data-stu-id="136fb-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="136fb-122">Dvě dimenze</span><span class="sxs-lookup"><span data-stu-id="136fb-122">Two Dimensions</span></span>  
 <span data-ttu-id="136fb-123">Některá pole mají dvě dimenze, jako je počet uzlů na každý floor každou vytváření aplikací na areálu.</span><span class="sxs-lookup"><span data-stu-id="136fb-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="136fb-124">Specifikace prvek vyžaduje číslo sestavení a dolní mez, a každý prvek obsahuje počet pro kombinaci budova a podlaží.</span><span class="sxs-lookup"><span data-stu-id="136fb-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="136fb-125">Proto se takové pole používá dva indexy.</span><span class="sxs-lookup"><span data-stu-id="136fb-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="136fb-126">Následující příklad deklaruje proměnnou pro uchování *dvourozměrné pole* počtu office pro 0 až 40 budovy a podlaží 0 až 5.</span><span class="sxs-lookup"><span data-stu-id="136fb-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="136fb-127">Dvourozměrné pole se také nazývá *pravoúhlého pole*.</span><span class="sxs-lookup"><span data-stu-id="136fb-127">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="136fb-128">Tři dimenze</span><span class="sxs-lookup"><span data-stu-id="136fb-128">Three Dimensions</span></span>  
 <span data-ttu-id="136fb-129">Několik pole mají tři dimenze, jako jsou hodnoty v trojrozměrném prostoru.</span><span class="sxs-lookup"><span data-stu-id="136fb-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="136fb-130">Tato pole používá tři indexy, které v tomto případě představují x, y a souřadnice z fyzického místa na disku.</span><span class="sxs-lookup"><span data-stu-id="136fb-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="136fb-131">Následující příklad deklaruje proměnnou pro uchování *trojrozměrného pole* air teploty v různých fázích trojrozměrného svazku.</span><span class="sxs-lookup"><span data-stu-id="136fb-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="136fb-132">Více než tři dimenze</span><span class="sxs-lookup"><span data-stu-id="136fb-132">More than Three Dimensions</span></span>  
 <span data-ttu-id="136fb-133">I když objekt array může mít až 32 rozměrů, zřídka dochází k mají více než tři.</span><span class="sxs-lookup"><span data-stu-id="136fb-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="136fb-134">Při přidání rozměry pole zvyšuje tak použití vícerozměrná pole s opatrností výrazně, celková velikost úložiště vyžadované pole.</span><span class="sxs-lookup"><span data-stu-id="136fb-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="136fb-135">Použití různých dimenzí</span><span class="sxs-lookup"><span data-stu-id="136fb-135">Using Different Dimensions</span></span>  
 <span data-ttu-id="136fb-136">Předpokládejme, že chcete sledovat objem prodeje za každý den tohoto měsíce.</span><span class="sxs-lookup"><span data-stu-id="136fb-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="136fb-137">Může prohlásit jednorozměrné pole s prvky 31, jeden pro každý den v měsíci jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="136fb-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="136fb-138">Nyní předpokládejme, že chcete sledovat stejné informace, nejen pro každý den v měsíci, ale také pro každý měsíc v roce.</span><span class="sxs-lookup"><span data-stu-id="136fb-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="136fb-139">Může prohlásit dvojrozměrné pole s 12 řádky (měsíců) a 31 sloupce (dny), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="136fb-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="136fb-140">Nyní předpokládejme, že se můžete rozhodnout, že se vaše pole obsahovat informace o více než jeden rok.</span><span class="sxs-lookup"><span data-stu-id="136fb-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="136fb-141">Pokud chcete sledovat objem prodeje po dobu 5 let, můžete deklarovat trojrozměrného pole s 5 vrstvy, 12 řádků a sloupců do 31, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="136fb-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="136fb-142">Všimněte si, že vzhledem k tomu, že každý index se liší od 0 na maximum, každé dimenze `salesAmounts` je deklarován jako jedna nižší než má požadovanou délku pro tuto dimenzi.</span><span class="sxs-lookup"><span data-stu-id="136fb-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="136fb-143">Všimněte si také, že velikost pole hodnota se zvyšuje s každou novou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="136fb-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="136fb-144">Tři velikosti v předchozích příkladech jsou 31, 372 a 1,860 elementy.</span><span class="sxs-lookup"><span data-stu-id="136fb-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="136fb-145">Můžete vytvořit pole bez použití `Dim` příkazu nebo `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="136fb-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="136fb-146">Například můžete volat <xref:System.Array.CreateInstance%2A> metody nebo jiné součásti předat kód pole vytvořené tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="136fb-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="136fb-147">Takový objekt array může mít dolní hranicí jinou než 0.</span><span class="sxs-lookup"><span data-stu-id="136fb-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="136fb-148">Můžete vždy otestovat pro dolní mez dimenze pomocí <xref:System.Array.GetLowerBound%2A> metoda nebo `LBound` funkce.</span><span class="sxs-lookup"><span data-stu-id="136fb-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136fb-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="136fb-149">See also</span></span>

- [<span data-ttu-id="136fb-150">Pole</span><span class="sxs-lookup"><span data-stu-id="136fb-150">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="136fb-151">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="136fb-151">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
