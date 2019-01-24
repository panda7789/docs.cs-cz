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
ms.openlocfilehash: 5ba92e113faf9d68bad97968937cc736132b2065
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708529"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="f2a8a-102">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2a8a-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="f2a8a-103">A *dimenze* je směr, ve kterém můžete měnit specifikace prvků tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="f2a8a-104">Pole, která obsahuje celkový prodej za každý den v měsíci má jednu dimenzi (den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="f2a8a-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="f2a8a-105">Pole, která obsahuje celkový prodej podle oddělení pro každý den v měsíci má dvě dimenze (číslo oddělení a den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="f2a8a-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="f2a8a-106">Počet rozměrů pole má nazývá jeho *pořadí*.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a8a-107">Můžete použít <xref:System.Array.Rank%2A> vlastnosti k určení, kolik rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="f2a8a-108">Práce s rozměry</span><span class="sxs-lookup"><span data-stu-id="f2a8a-108">Working with Dimensions</span></span>  
 <span data-ttu-id="f2a8a-109">Určit element pole zadáním *index* nebo *dolní index* pro každé své dimenze.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="f2a8a-110">Prvky jsou souvislé podél každé dimenze od indexu 0 až po nejvyšší index pro tuto dimenzi.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="f2a8a-111">Na následujících obrázcích je koncepční struktura polí se různé rozměry.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="f2a8a-112">Každý prvek na obrázcích zobrazuje hodnoty indexu, které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="f2a8a-113">Například můžete přístup k první prvek druhého řádku dvourozměrné pole tak, že zadáte indexy `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="f2a8a-114">![Grafický diagram jednoho&#45;jednorozměrné pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="f2a8a-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="f2a8a-115">Jednorozměrné pole</span><span class="sxs-lookup"><span data-stu-id="f2a8a-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="f2a8a-116">![Grafický diagram dvou&#45;jednorozměrné pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="f2a8a-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="f2a8a-117">dvourozměrné pole</span><span class="sxs-lookup"><span data-stu-id="f2a8a-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="f2a8a-118">![Grafický diagram tři&#45;jednorozměrné pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="f2a8a-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="f2a8a-119">trojrozměrného pole</span><span class="sxs-lookup"><span data-stu-id="f2a8a-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="f2a8a-120">Jedna dimenze</span><span class="sxs-lookup"><span data-stu-id="f2a8a-120">One Dimension</span></span>  
 <span data-ttu-id="f2a8a-121">Mnoho pole mají pouze jednu dimenzi, například počet lidí každý věk.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="f2a8a-122">Chcete-li určit element Jediným požadavkem je věk, pro které tento prvek obsahuje počet.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="f2a8a-123">Proto se takové pole používá pouze jeden index.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="f2a8a-124">Následující příklad deklaruje proměnnou pro uchování *jednorozměrné pole* věku se počítá od 0 až 120.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="f2a8a-125">Dvě dimenze</span><span class="sxs-lookup"><span data-stu-id="f2a8a-125">Two Dimensions</span></span>  
 <span data-ttu-id="f2a8a-126">Některá pole mají dvě dimenze, jako je počet uzlů na každý floor každou vytváření aplikací na areálu.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="f2a8a-127">Specifikace prvek vyžaduje číslo sestavení a dolní mez, a každý prvek obsahuje počet pro kombinaci budova a podlaží.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="f2a8a-128">Proto se takové pole používá dva indexy.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="f2a8a-129">Následující příklad deklaruje proměnnou pro uchování *dvourozměrné pole* počtu office pro 0 až 40 budovy a podlaží 0 až 5.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="f2a8a-130">Dvourozměrné pole se také nazývá *pravoúhlého pole*.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="f2a8a-131">Tři dimenze</span><span class="sxs-lookup"><span data-stu-id="f2a8a-131">Three Dimensions</span></span>  
 <span data-ttu-id="f2a8a-132">Několik pole mají tři dimenze, jako jsou hodnoty v trojrozměrném prostoru.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="f2a8a-133">Tato pole používá tři indexy, které v tomto případě představují x, y a souřadnice z fyzického místa na disku.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="f2a8a-134">Následující příklad deklaruje proměnnou pro uchování *trojrozměrného pole* air teploty v různých fázích trojrozměrného svazku.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="f2a8a-135">Více než tři dimenze</span><span class="sxs-lookup"><span data-stu-id="f2a8a-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="f2a8a-136">I když objekt array může mít až 32 rozměrů, zřídka dochází k mají více než tři.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a8a-137">Při přidání rozměry pole zvyšuje tak použití vícerozměrná pole s opatrností výrazně, celková velikost úložiště vyžadované pole.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="f2a8a-138">Použití různých dimenzí</span><span class="sxs-lookup"><span data-stu-id="f2a8a-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="f2a8a-139">Předpokládejme, že chcete sledovat objem prodeje za každý den tohoto měsíce.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="f2a8a-140">Může prohlásit jednorozměrné pole s prvky 31, jeden pro každý den v měsíci jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="f2a8a-141">Nyní předpokládejme, že chcete sledovat stejné informace, nejen pro každý den v měsíci, ale také pro každý měsíc v roce.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="f2a8a-142">Může prohlásit dvojrozměrné pole s 12 řádky (měsíců) a 31 sloupce (dny), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="f2a8a-143">Nyní předpokládejme, že se můžete rozhodnout, že se vaše pole obsahovat informace o více než jeden rok.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="f2a8a-144">Pokud chcete sledovat objem prodeje po dobu 5 let, můžete deklarovat trojrozměrného pole s 5 vrstvy, 12 řádků a sloupců do 31, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="f2a8a-145">Všimněte si, že vzhledem k tomu, že každý index se liší od 0 na maximum, každé dimenze `salesAmounts` je deklarován jako jedna nižší než má požadovanou délku pro tuto dimenzi.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="f2a8a-146">Všimněte si také, že velikost pole hodnota se zvyšuje s každou novou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="f2a8a-147">Tři velikosti v předchozích příkladech jsou 31, 372 a 1,860 elementy.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a8a-148">Můžete vytvořit pole bez použití `Dim` příkazu nebo `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="f2a8a-149">Například můžete volat <xref:System.Array.CreateInstance%2A> metody nebo jiné součásti předat kód pole vytvořené tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="f2a8a-150">Takový objekt array může mít dolní hranicí jinou než 0.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="f2a8a-151">Můžete vždy otestovat pro dolní mez dimenze pomocí <xref:System.Array.GetLowerBound%2A> metoda nebo `LBound` funkce.</span><span class="sxs-lookup"><span data-stu-id="f2a8a-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a8a-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2a8a-152">See also</span></span>
- [<span data-ttu-id="f2a8a-153">Pole</span><span class="sxs-lookup"><span data-stu-id="f2a8a-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f2a8a-154">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="f2a8a-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
