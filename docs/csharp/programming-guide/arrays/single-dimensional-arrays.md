---
title: Jednorozměrná pole – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170348"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="313c3-102">Jednorozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="313c3-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="313c3-103">Můžete deklarovat jednorozměrné pole pěti celočísel, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="313c3-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="313c3-104">Toto pole obsahuje `array[0]` `array[4]`prvky z do .</span><span class="sxs-lookup"><span data-stu-id="313c3-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="313c3-105">[Nový](../../language-reference/operators/new-operator.md) operátor se používá k vytvoření pole a inicializaci prvků pole na jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="313c3-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="313c3-106">V tomto příkladu jsou všechny prvky pole inicializovány na nulu.</span><span class="sxs-lookup"><span data-stu-id="313c3-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="313c3-107">Pole, které ukládá řetězcové prvky, může být deklarováno stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="313c3-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="313c3-108">Například:</span><span class="sxs-lookup"><span data-stu-id="313c3-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="313c3-109">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="313c3-109">Array Initialization</span></span>

 <span data-ttu-id="313c3-110">Je možné inicializovat pole při deklaraci, v takovém případě není specifikátor délky nutný, protože je již zadán počtem prvků v inicializačním seznamu.</span><span class="sxs-lookup"><span data-stu-id="313c3-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="313c3-111">Například:</span><span class="sxs-lookup"><span data-stu-id="313c3-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="313c3-112">Pole řetězce lze inicializovat stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="313c3-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="313c3-113">Následuje deklarace pole řetězců, kde je každý prvek pole inicializován názvem dne:</span><span class="sxs-lookup"><span data-stu-id="313c3-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="313c3-114">Při inicializaci pole při deklaraci můžete použít následující zkratky:</span><span class="sxs-lookup"><span data-stu-id="313c3-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="313c3-115">Je možné deklarovat proměnnou pole bez inicializace, ale je nutné použít `new` operátor při přiřazení pole k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="313c3-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="313c3-116">Například:</span><span class="sxs-lookup"><span data-stu-id="313c3-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="313c3-117">C# 3.0 zavádí implicitně zadaných polí.</span><span class="sxs-lookup"><span data-stu-id="313c3-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="313c3-118">Další informace naleznete [v tématu Implicitně zadali pole](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="313c3-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="313c3-119">Pole typu a referenčního typu</span><span class="sxs-lookup"><span data-stu-id="313c3-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="313c3-120">Zvažte následující deklaraci pole:</span><span class="sxs-lookup"><span data-stu-id="313c3-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="313c3-121">Výsledek tohoto příkazu závisí `SomeType` na tom, zda je typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="313c3-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="313c3-122">Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="313c3-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="313c3-123">Pokud `SomeType` je typ odkazu, příkaz vytvoří pole 10 prvků, z nichž každý je inicializován na odkaz null.</span><span class="sxs-lookup"><span data-stu-id="313c3-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="313c3-124">Další informace o typech hodnot a typech odkazů naleznete v [tématu Typy hodnot](../../language-reference/builtin-types/value-types.md) a [Reference .](../../language-reference/keywords/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="313c3-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="313c3-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="313c3-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="313c3-126">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="313c3-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="313c3-127">Pole</span><span class="sxs-lookup"><span data-stu-id="313c3-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="313c3-128">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="313c3-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="313c3-129">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="313c3-129">Jagged Arrays</span></span>](./jagged-arrays.md)
