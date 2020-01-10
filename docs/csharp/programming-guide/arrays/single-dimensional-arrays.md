---
title: Jednorozměrná pole – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 07c6061bfc66b1640d0eacca217302feff1a390a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715032"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="bafef-102">Jednorozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bafef-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="bafef-103">Můžete deklarovat jednorozměrné pole pěti celých čísel, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bafef-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="bafef-104">Toto pole obsahuje prvky z `array[0]` k `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="bafef-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="bafef-105">Operátor [New](../../language-reference/operators/new-operator.md) slouží k vytvoření pole a inicializaci prvků pole na jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bafef-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="bafef-106">V tomto příkladu jsou všechny prvky pole inicializovány na nulu.</span><span class="sxs-lookup"><span data-stu-id="bafef-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="bafef-107">Pole, které ukládá prvky řetězce, lze deklarovat stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="bafef-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="bafef-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bafef-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="bafef-109">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="bafef-109">Array Initialization</span></span>

 <span data-ttu-id="bafef-110">Je možné inicializovat pole po deklaraci, v takovém případě není specifikátor délky nutný, protože je již poskytnutý počtem prvků v seznamu inicializace.</span><span class="sxs-lookup"><span data-stu-id="bafef-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="bafef-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bafef-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="bafef-112">Pole řetězců lze inicializovat stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="bafef-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="bafef-113">Následuje deklarace pole řetězců, kde je každý element pole inicializován pomocí názvu dne:</span><span class="sxs-lookup"><span data-stu-id="bafef-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="bafef-114">Když inicializujete pole při deklaraci, můžete použít následující klávesové zkratky:</span><span class="sxs-lookup"><span data-stu-id="bafef-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="bafef-115">Je možné deklarovat proměnnou pole bez inicializace, ale je nutné použít operátor `new`, když přiřadíte pole k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="bafef-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="bafef-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bafef-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="bafef-117">C#3,0 zavádí implicitně typované pole.</span><span class="sxs-lookup"><span data-stu-id="bafef-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="bafef-118">Další informace naleznete v tématu [implicitně typované pole](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bafef-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="bafef-119">Pole Typ hodnoty a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="bafef-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="bafef-120">Zvažte následující deklaraci pole:</span><span class="sxs-lookup"><span data-stu-id="bafef-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="bafef-121">Výsledek tohoto příkazu závisí na tom, zda `SomeType` typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="bafef-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="bafef-122">Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="bafef-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="bafef-123">Pokud je `SomeType` odkazový typ, příkaz vytvoří pole 10 prvků, z nichž každá je inicializována na odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="bafef-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="bafef-124">Další informace o typech hodnot a odkazových typech naleznete v tématu [typy hodnot](../../language-reference/keywords/value-types.md) a [odkazové typy](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="bafef-124">For more information about value types and reference types, see [Value types](../../language-reference/keywords/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bafef-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bafef-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="bafef-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bafef-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bafef-127">Pole</span><span class="sxs-lookup"><span data-stu-id="bafef-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="bafef-128">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="bafef-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="bafef-129">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="bafef-129">Jagged Arrays</span></span>](./jagged-arrays.md)
