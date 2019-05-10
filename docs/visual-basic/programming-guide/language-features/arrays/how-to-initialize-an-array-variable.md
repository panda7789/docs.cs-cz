---
title: 'Postupy: Inicializace proměnné pole v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 0e450a370c27de4690105231847de25ce5a90553
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627456"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="19928-102">Postupy: Inicializace proměnné pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19928-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="19928-103">Inicializujte proměnnou pole včetně literálu pole v `New` klauzule a určením počáteční hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="19928-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="19928-104">Můžete zadat typ nebo umožnit jeho odvození z hodnot v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="19928-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="19928-105">Další informace o tom, jak je odvozený typ, naleznete v tématu "Vyplnění pole počátečními hodnotami" v [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="19928-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="19928-106">Inicializace proměnné pole pomocí literálu pole</span><span class="sxs-lookup"><span data-stu-id="19928-106">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="19928-107">Buď `New` klauzuli, nebo když přiřadíte hodnotu pole, zadejte hodnoty elementů uvnitř závorek (`{}`).</span><span class="sxs-lookup"><span data-stu-id="19928-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="19928-108">Následující příklad ukazuje několik způsobů, jak deklarovat, vytvářet a inicializovat proměnnou tak, aby obsahovala pole s prvky typu `Char`.</span><span class="sxs-lookup"><span data-stu-id="19928-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="19928-109">Po spuštění všech příkazů má vytvořené pole délku 3, přičemž prvky v indexu 0 až 2 obsahují počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="19928-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="19928-110">Pokud zadáte horní mez a hodnoty, je nutné zahrnout hodnotu pro každý prvek od indexu 0 až po horní mez.</span><span class="sxs-lookup"><span data-stu-id="19928-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="19928-111">Všimněte si, že nemusíte určit horní mez indexu, pokud zadáte hodnoty elementu v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="19928-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="19928-112">Pokud není zadána žádná horní mez, velikost pole odvozena na základě počtu hodnot literálu pole.</span><span class="sxs-lookup"><span data-stu-id="19928-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="19928-113">Inicializace vícedimenzovaného pole pomocí literálů pole</span><span class="sxs-lookup"><span data-stu-id="19928-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="19928-114">Vnořené hodnoty uvnitř složených závorek (`{}`) v závorkách.</span><span class="sxs-lookup"><span data-stu-id="19928-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="19928-115">Ujistěte se, že jsou vnořené literály pole, které všechny odvozené jako pole stejného typu a délky.</span><span class="sxs-lookup"><span data-stu-id="19928-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="19928-116">Následující příklad kódu ukazuje několik příkladů inicializace multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="19928-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="19928-117">Můžete explicitně určit hranice pole nebo je vynechat a nechat kompilátor odvodit hranice pole na základě hodnot v literálu pole.</span><span class="sxs-lookup"><span data-stu-id="19928-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="19928-118">Pokud zadáte horní mez a hodnoty, je nutné zahrnout hodnotu pro každý prvek od indexu 0 až po horní mez v každém rozměru.</span><span class="sxs-lookup"><span data-stu-id="19928-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="19928-119">Následující příklad ukazuje několik způsobů, jak deklarovat, vytvářet a inicializovat proměnnou tak, aby obsahovala dvojrozměrné pole obsahující prvky typu `Short`</span><span class="sxs-lookup"><span data-stu-id="19928-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="19928-120">Po spuštění všech příkazů obsahuje vytvořené pole šest inicializovaných prvků s indexy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, a `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="19928-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="19928-121">Každé umístění pole obsahuje hodnotu `10`.</span><span class="sxs-lookup"><span data-stu-id="19928-121">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="19928-122">Následující příklad provede iteraci multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="19928-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="19928-123">V konzolové aplikaci Windows, která je napsána v jazyce Visual Basic, vložte kód do `Sub Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="19928-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="19928-124">Poslední komentáře popisují výstup.</span><span class="sxs-lookup"><span data-stu-id="19928-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="19928-125">Inicializace proměnné vícenásobného pole pomocí literálů pole</span><span class="sxs-lookup"><span data-stu-id="19928-125">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="19928-126">Hodnoty objektu vložte uvnitř složených závorek (`{}`).</span><span class="sxs-lookup"><span data-stu-id="19928-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="19928-127">Ačkoli lze také vnořit literály pole, které specifikují pole různé délky, v případě vícenásobného pole, ujistěte se, že jsou vnořené literály pole uzavřeny do závorek (`()`).</span><span class="sxs-lookup"><span data-stu-id="19928-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="19928-128">Závorky vynutí vyhodnocení literály vnořeného pole a výsledná pole jsou použita jako počáteční hodnoty vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="19928-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="19928-129">Následující příklad kódu ukazuje dva příklady inicializace vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="19928-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="19928-130">Následující příklad provede iteraci vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="19928-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="19928-131">V konzolové aplikaci Windows, která je napsána v jazyce Visual Basic, vložte kód do `Sub Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="19928-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="19928-132">Poslední komentáře v kódu popisují výstup.</span><span class="sxs-lookup"><span data-stu-id="19928-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="19928-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19928-133">See also</span></span>

- [<span data-ttu-id="19928-134">Pole</span><span class="sxs-lookup"><span data-stu-id="19928-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="19928-135">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="19928-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
