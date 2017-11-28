---
title: "Rozměry pole v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="f2f0e-102">Rozměry pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2f0e-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="f2f0e-103">A *dimenze* je směr, ve kterém můžete měnit specifikace elementů tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="f2f0e-104">Pole, které obsahuje celkový počet prodeje za každý den v měsíci má jednu dimenzi (den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="f2f0e-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="f2f0e-105">Pole, které obsahuje celkový počet prodeje podle oddělení pro každý den v měsíci se dvěma rozměry (číslo oddělení a den v měsíci).</span><span class="sxs-lookup"><span data-stu-id="f2f0e-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="f2f0e-106">Počet dimenzí pole se nazývá jeho *pořadí*.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f0e-107">Můžete použít <xref:System.Array.Rank%2A> vlastnosti k určení, kolik rozměry pole.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="f2f0e-108">Práce s dimenzí</span><span class="sxs-lookup"><span data-stu-id="f2f0e-108">Working with Dimensions</span></span>  
 <span data-ttu-id="f2f0e-109">Zadejte k elementu pole zadáním *index* nebo *dolní index* pro každou z jeho dimenzí.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="f2f0e-110">Elementy jsou souvislé každý dimenzi z indexu 0 prostřednictvím nejvyšší index pro daná dimenze.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="f2f0e-111">Následující ilustrace znázorňuje koncepční strukturu polí se různá pořadí.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="f2f0e-112">Každý prvek v tyto ilustrace zobrazuje hodnoty indexu, které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="f2f0e-113">Například můžete první prvek pole dvourozměrná druhý řádek přístup zadáním indexy `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="f2f0e-114">![Grafický diagram jeden & č. 45; dimenzí pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="f2f0e-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="f2f0e-115">Jednorozměrné pole</span><span class="sxs-lookup"><span data-stu-id="f2f0e-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="f2f0e-116">![Grafický diagram dva & č. 45; dimenzí pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="f2f0e-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="f2f0e-117">Dvourozměrná pole</span><span class="sxs-lookup"><span data-stu-id="f2f0e-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="f2f0e-118">![Grafický diagram tři & č. 45; dimenzí pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="f2f0e-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="f2f0e-119">trojrozměrné pole</span><span class="sxs-lookup"><span data-stu-id="f2f0e-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="f2f0e-120">Jednu dimenzi</span><span class="sxs-lookup"><span data-stu-id="f2f0e-120">One Dimension</span></span>  
 <span data-ttu-id="f2f0e-121">Mnoho pole mají jenom jednou dimenzí, jako je například počet lidí každý věk.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="f2f0e-122">Jediným požadavkem k určení element je stáří, pro které daný element obsahuje počet.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="f2f0e-123">Proto tyto pole používá jenom jeden index.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="f2f0e-124">Následující příklad deklaruje proměnnou pro uložení *jednorozměrné pole* věku počty od 0 do 120.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="f2f0e-125">Dvě dimenze</span><span class="sxs-lookup"><span data-stu-id="f2f0e-125">Two Dimensions</span></span>  
 <span data-ttu-id="f2f0e-126">Některé pole mají dvě dimenze, jako je počet uzlů na každý podlaží každý vytváření ve kanceláře.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="f2f0e-127">Specifikace elementu vyžaduje číslo sestavení a podlaží a každý prvek obsahuje počet pro tuto kombinaci budova a podlaží.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="f2f0e-128">Proto tyto pole používá dva indexy.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="f2f0e-129">Následující příklad deklaruje proměnnou pro uložení *dvourozměrná pole* office součtů pro 0 až 40 budovy a podlaží 0 až 5.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="f2f0e-130">Je také označován dvourozměrná pole *obdélníková pole*.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="f2f0e-131">Tři dimenze</span><span class="sxs-lookup"><span data-stu-id="f2f0e-131">Three Dimensions</span></span>  
 <span data-ttu-id="f2f0e-132">Několik polí mít tři dimenzí, jako je například hodnoty v trojrozměrné prostoru.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="f2f0e-133">Takové pole používá tři indexy, které v tomto případě představují x, y a souřadnice z fyzického místa na disku.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="f2f0e-134">Následující příklad deklaruje proměnnou pro uložení *trojrozměrné* z teploty letecké v různých fázích trojrozměrné svazku.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="f2f0e-135">Víc než třemi dimenze</span><span class="sxs-lookup"><span data-stu-id="f2f0e-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="f2f0e-136">I když pole může mít maximálně 32 dimenzí, je výjimečná mít víc než tři.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f0e-137">Když přidáte dimenze do pole, zvyšuje celkové úložiště vyžaduje pole podstatně, tak vícerozměrná pole použití dát pozor.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="f2f0e-138">Pomocí různých dimenzí</span><span class="sxs-lookup"><span data-stu-id="f2f0e-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="f2f0e-139">Předpokládejme, že chcete sledovat částek prodeje pro každý den v měsíci přítomen.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="f2f0e-140">Může deklarovat jednorozměrné pole s 31 prvky, jednu pro každý den v měsíci jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="f2f0e-141">Nyní předpokládejme, že chcete sledovat stejné informace, ne jenom pro každý den v měsíci, ale také pro každý měsíc v roce.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="f2f0e-142">Může deklarovat dvourozměrná pole s 12 řádků (pro měsíců) a 31 sloupců (pro dny), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="f2f0e-143">Nyní předpokládejme, že se můžete rozhodnout, že se vaše pole obsahovat informace o více než jeden rok.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="f2f0e-144">Pokud chcete sledovat částek prodeje 5 let, může deklarovat trojrozměrné s 5 vrstev, 12 řádků a sloupců 31, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="f2f0e-145">Všimněte si, že, protože každý index se liší od 0 do jeho maximální každé dimenze `salesAmounts` je deklarován jako jeden menší než má požadovanou délku dané dimenze.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="f2f0e-146">Všimněte si také, že velikost pole hodnota se zvyšuje s každou novou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="f2f0e-147">Tři velikosti v předchozích ukázkách jsou 31, 372 a 1,860 elementy.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f0e-148">Můžete vytvořit pole bez použití `Dim` příkaz nebo `New` klauzule.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="f2f0e-149">Například můžete volat <xref:System.Array.CreateInstance%2A> metody nebo jiné komponenty můžete předat kódu matice vytvořené tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="f2f0e-150">Takové pole může mít dolní mez než 0.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="f2f0e-151">Můžete se pro dolní hranice dimenze pomocí vždy otestovat <xref:System.Array.GetLowerBound%2A> metoda nebo `LBound` funkce.</span><span class="sxs-lookup"><span data-stu-id="f2f0e-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f0e-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2f0e-152">See Also</span></span>  
 [<span data-ttu-id="f2f0e-153">Pole</span><span class="sxs-lookup"><span data-stu-id="f2f0e-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="f2f0e-154">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="f2f0e-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
