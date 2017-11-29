---
title: "Postupy: Inicializace proměnné pole v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="20a72-102">Postupy: Inicializace proměnné pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20a72-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="20a72-103">Inicializace proměnné pole zahrnutím literál v pole `New` klauzule a zadat počáteční hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="20a72-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="20a72-104">Můžete buď zadat typ nebo umožněte její odvodit z hodnot v poli literálu.</span><span class="sxs-lookup"><span data-stu-id="20a72-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="20a72-105">Další informace o tom, jak je odvodit typ, najdete v části "Vyplní pole s počáteční hodnoty" v [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="20a72-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="20a72-106">Inicializace proměnné pole s použitím pole literálu</span><span class="sxs-lookup"><span data-stu-id="20a72-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="20a72-107">Buď v `New` klauzuli, nebo když přiřazujete hodnota pole, zadejte hodnoty element uvnitř složené závorky (`{}`).</span><span class="sxs-lookup"><span data-stu-id="20a72-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="20a72-108">Následující příklad znázorňuje několik způsobů, jak deklarovat, vytvoření a inicializace proměnnou, která bude obsahovat pole, které má elementy typu `Char`.</span><span class="sxs-lookup"><span data-stu-id="20a72-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="20a72-109">Po provedení každého příkazu, pole, která je vytvořena má délku 3 s prvky na pozici 0 prostřednictvím index 2 obsahující počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="20a72-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="20a72-110">Pokud zadáte horní mez a hodnoty, musí obsahovat hodnotu pro každý element z indexu 0 prostřednictvím horní mez.</span><span class="sxs-lookup"><span data-stu-id="20a72-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="20a72-111">Všimněte si, že nemáte zadejte index horní mez, pokud zadáte hodnoty prvků v matici literálu.</span><span class="sxs-lookup"><span data-stu-id="20a72-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="20a72-112">Pokud není zadaný žádný horní mez, je velikost pole odvodit na základě počtu hodnot v poli literálu.</span><span class="sxs-lookup"><span data-stu-id="20a72-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="20a72-113">K chybě při inicializaci proměnnou multidimenzionálního pole pomocí pole literály</span><span class="sxs-lookup"><span data-stu-id="20a72-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="20a72-114">Vnořit hodnoty v závorkách (`{}`) v rámci složené závorky.</span><span class="sxs-lookup"><span data-stu-id="20a72-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="20a72-115">Zajistěte, aby literály vnořená pole, které všechny odvození jako pole stejného typu a délka.</span><span class="sxs-lookup"><span data-stu-id="20a72-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="20a72-116">Následující příklad kódu ukazuje několik příkladů, inicializace multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="20a72-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="20a72-117">Můžete explicitně zadat rozsah pole nebo je vynecháte a mít kompilátoru odvození meze pole na základě hodnot v poli literálu.</span><span class="sxs-lookup"><span data-stu-id="20a72-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="20a72-118">Pokud zadáte horní hranice a hodnoty, musí obsahovat hodnotu pro každý element z indexu 0 prostřednictvím horní hranice v každé dimenze.</span><span class="sxs-lookup"><span data-stu-id="20a72-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="20a72-119">Následující příklad znázorňuje několik způsobů, jak deklarovat, vytvoření a inicializace proměnné tak, aby obsahovala dvourozměrná pole, která má elementy typu`Short`</span><span class="sxs-lookup"><span data-stu-id="20a72-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="20a72-120">Po provedení každého příkazu, vytvořené pole obsahuje šest inicializovaného prvky, které mají indexy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, a `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="20a72-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="20a72-121">Každé pole umístění obsahuje hodnotu `10`.</span><span class="sxs-lookup"><span data-stu-id="20a72-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="20a72-122">V následujícím příkladu prochází multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="20a72-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="20a72-123">V aplikaci konzoly systému Windows, který je napsán v jazyce Visual Basic, vložte kód do `Sub Main()` metoda.</span><span class="sxs-lookup"><span data-stu-id="20a72-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="20a72-124">Poslední komentáře zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="20a72-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="20a72-125">K chybě při inicializaci proměnnou Vícenásobná pole pomocí pole literály</span><span class="sxs-lookup"><span data-stu-id="20a72-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="20a72-126">Vnořit hodnoty objektu uvnitř složené závorky (`{}`).</span><span class="sxs-lookup"><span data-stu-id="20a72-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="20a72-127">I když lze také vnořit literály pole, které určují pole různých délek, v případě Vícenásobná pole, ujistěte se, že který literály vnořená pole jsou uzavřené v závorkách (`()`).</span><span class="sxs-lookup"><span data-stu-id="20a72-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="20a72-128">Závorky vynutit vyhodnocení literály vnořená pole a pole výsledné jsou použity jako počáteční hodnoty Vícenásobná pole.</span><span class="sxs-lookup"><span data-stu-id="20a72-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="20a72-129">Následující příklad kódu ukazuje dva příklady inicializace Vícenásobná pole.</span><span class="sxs-lookup"><span data-stu-id="20a72-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="20a72-130">V následujícím příkladu prochází Vícenásobná pole.</span><span class="sxs-lookup"><span data-stu-id="20a72-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="20a72-131">V aplikaci konzoly systému Windows, který je napsán v jazyce Visual Basic, vložte kód do `Sub Main()` metoda.</span><span class="sxs-lookup"><span data-stu-id="20a72-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="20a72-132">Poslední komentáře v kódu zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="20a72-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20a72-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="20a72-133">See Also</span></span>  
 [<span data-ttu-id="20a72-134">Pole</span><span class="sxs-lookup"><span data-stu-id="20a72-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="20a72-135">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="20a72-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
