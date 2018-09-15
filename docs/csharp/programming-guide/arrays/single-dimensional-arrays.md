---
title: Jednorozměrná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: c2f26fd74a596ada21eef578e58c9cd8e0305d6c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616218"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="9a1b7-102">Jednorozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9a1b7-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="9a1b7-103">Je možné deklarovat jednorozměrné pole pět celých čísel, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 <span data-ttu-id="9a1b7-104">Toto pole obsahuje prvky z `array[0]` k `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="9a1b7-105">[Nové](../../../csharp/language-reference/keywords/new.md) operátor se používá k vytvoření pole a inicializaci prvků pole na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-105">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="9a1b7-106">V tomto příkladu jsou všechny prvky pole inicializovány na nulu.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="9a1b7-107">Pole, která ukládá prvků řetězce mohou být deklarovány stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="9a1b7-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="9a1b7-109">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="9a1b7-109">Array Initialization</span></span>

 <span data-ttu-id="9a1b7-110">Je možné k inicializaci pole při deklaraci, v takovém případě není potřeba specifikátor pozice, protože je už zadaný počet prvků v inicializačního seznamu.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-110">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="9a1b7-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 <span data-ttu-id="9a1b7-112">Pole řetězců mohou být inicializovány stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="9a1b7-113">Následuje deklaraci pole řetězců kde každý prvek pole je inicializována pomocí názvu dne:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 <span data-ttu-id="9a1b7-114">Když inicializujete pole při deklaraci, můžete použít následující klávesové zkratky:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 <span data-ttu-id="9a1b7-115">Je možné deklarovat proměnné pole bez inicializace, ale je nutné použít `new` operátor při přiřazení k této proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="9a1b7-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 <span data-ttu-id="9a1b7-117">C# 3.0 zavádí implicitně typovaná pole.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="9a1b7-118">Další informace najdete v tématu [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="9a1b7-118">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="9a1b7-119">Typ hodnoty a odkaz na typ pole</span><span class="sxs-lookup"><span data-stu-id="9a1b7-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="9a1b7-120">Vezměte v úvahu následující deklarace pole:</span><span class="sxs-lookup"><span data-stu-id="9a1b7-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 <span data-ttu-id="9a1b7-121">Výsledkem tohoto příkazu závisí na tom, zda `SomeType` je hodnotový typ nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="9a1b7-122">Pokud je typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každá má typ `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="9a1b7-123">Pokud `SomeType` je typem odkazu, příkaz vytvoří pole 10 prvků, z nichž každý je inicializován na hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="9a1b7-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="9a1b7-124">Další informace o typy hodnot a typy odkazů, najdete v části [typy](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="9a1b7-124">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1b7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a1b7-125">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="9a1b7-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a1b7-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9a1b7-127">Pole</span><span class="sxs-lookup"><span data-stu-id="9a1b7-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="9a1b7-128">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="9a1b7-128">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="9a1b7-129">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="9a1b7-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
