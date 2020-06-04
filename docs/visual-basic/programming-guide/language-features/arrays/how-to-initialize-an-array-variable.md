---
title: 'Postupy: Inicializace proměnné pole'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 7feaf71fa1c59c24aa751f2b9e28328d47ba357c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413063"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="d19d1-102">Postupy: Inicializace proměnné pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d19d1-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="d19d1-103">Inicializujete proměnnou pole zahrnutím literálu pole do `New` klauzule a určením počátečních hodnot pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="d19d1-104">Můžete buď zadat typ, nebo ho nechat odvoditelné z hodnot v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="d19d1-105">Další informace o tom, jak je typ odvozen, naleznete v části "vyplnění pole počátečními hodnotami" v [polích](index.md).</span><span class="sxs-lookup"><span data-stu-id="d19d1-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="d19d1-106">Inicializace proměnné pole pomocí literálu pole</span><span class="sxs-lookup"><span data-stu-id="d19d1-106">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="d19d1-107">Buď v `New` klauzuli, nebo při přiřazení hodnoty pole zadejte hodnoty elementu do složených závorek ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="d19d1-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="d19d1-108">Následující příklad ukazuje několik způsobů, jak deklarovat, vytvořit a inicializovat proměnnou tak, aby obsahovala pole s prvky typu `Char` .</span><span class="sxs-lookup"><span data-stu-id="d19d1-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="d19d1-109">Po spuštění každého příkazu má pole vytvořené délku 3 s prvky v indexu 0 až index 2 obsahující počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d19d1-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="d19d1-110">Pokud zadáte horní mez a hodnoty, je nutné zahrnout hodnotu pro každý prvek z indexu 0 až po horní mez.</span><span class="sxs-lookup"><span data-stu-id="d19d1-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="d19d1-111">Všimněte si, že není nutné zadat horní mez indexu, pokud zadáváte hodnoty prvků v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="d19d1-112">Pokud není zadána žádná horní mez, je velikost pole odvozena v závislosti na počtu hodnot v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="d19d1-113">Inicializace proměnné multidimenzionálního pole pomocí literálů pole</span><span class="sxs-lookup"><span data-stu-id="d19d1-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="d19d1-114">Vnořit hodnoty do složených závorek ( `{}` ) uvnitř složených závorek ().</span><span class="sxs-lookup"><span data-stu-id="d19d1-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="d19d1-115">Zajistěte, aby literály vnořeného pole byly odvozeny jako pole stejného typu a délky.</span><span class="sxs-lookup"><span data-stu-id="d19d1-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="d19d1-116">Následující příklad kódu ukazuje několik příkladů inicializace multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="d19d1-117">Můžete explicitně zadat hranice pole nebo je nechat vypnout a nechat kompilátor odvodit hranice pole na základě hodnot v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="d19d1-118">Pokud zadáte horní meze i hodnoty, je nutné zahrnout hodnotu pro každý prvek z indexu 0 až po horní mez v každé dimenzi.</span><span class="sxs-lookup"><span data-stu-id="d19d1-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="d19d1-119">Následující příklad ukazuje několik způsobů, jak deklarovat, vytvořit a inicializovat proměnnou tak, aby obsahovala dvourozměrné pole, které má prvky typu`Short`</span><span class="sxs-lookup"><span data-stu-id="d19d1-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="d19d1-120">Po spuštění každého příkazu obsahuje vytvořené pole šest inicializovaných prvků, které mají indexy `(0,0)` , `(0,1)` ,,, `(0,2)` `(1,0)` `(1,1)` a `(1,2)` .</span><span class="sxs-lookup"><span data-stu-id="d19d1-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="d19d1-121">Každé umístění pole obsahuje hodnotu `10` .</span><span class="sxs-lookup"><span data-stu-id="d19d1-121">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="d19d1-122">Následující příklad provede iteraci multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="d19d1-123">V konzolové aplikaci systému Windows, která je napsána v Visual Basic, vložte kód do `Sub Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="d19d1-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="d19d1-124">Poslední komentáře ukazují výstup.</span><span class="sxs-lookup"><span data-stu-id="d19d1-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="d19d1-125">Inicializace proměnné vícenásobného pole pomocí literálů pole</span><span class="sxs-lookup"><span data-stu-id="d19d1-125">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="d19d1-126">Hodnoty vnořených objektů do složených závorek ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="d19d1-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="d19d1-127">I když lze také vnořit literály pole, které určují pole různých délek, v případě vícenásobného pole se ujistěte, že literály vnořeného pole jsou uzavřeny v závorkách ( `()` ).</span><span class="sxs-lookup"><span data-stu-id="d19d1-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="d19d1-128">Závorky vynutí vyhodnocení literálů vnořeného pole a výsledná pole se používají jako počáteční hodnoty nevícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="d19d1-129">Následující příklad kódu ukazuje dva příklady inicializace vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="d19d1-130">Následující příklad projde vícenásobné pole.</span><span class="sxs-lookup"><span data-stu-id="d19d1-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="d19d1-131">V konzolové aplikaci systému Windows, která je napsána v Visual Basic, vložte kód do `Sub Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="d19d1-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="d19d1-132">Poslední komentáře v kódu ukazují výstup.</span><span class="sxs-lookup"><span data-stu-id="d19d1-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="d19d1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d19d1-133">See also</span></span>

- [<span data-ttu-id="d19d1-134">Pole</span><span class="sxs-lookup"><span data-stu-id="d19d1-134">Arrays</span></span>](index.md)
- [<span data-ttu-id="d19d1-135">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="d19d1-135">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
