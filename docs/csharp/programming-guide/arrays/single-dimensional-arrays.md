---
title: Jednorozměrná pole – Průvodce programováním v C#
description: Vytvořte jednorozměrné pole v jazyce C# pomocí operátoru new určujícího typ prvku pole a počet prvků.
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474589"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="a892e-103">Jednorozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a892e-103">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="a892e-104">Vytvoříte jednorozměrné pole pomocí operátoru [New](../../language-reference/operators/new-operator.md) , který určuje typ prvku pole a počet prvků.</span><span class="sxs-lookup"><span data-stu-id="a892e-104">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="a892e-105">Následující příklad deklaruje pole pěti celých čísel:</span><span class="sxs-lookup"><span data-stu-id="a892e-105">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="a892e-106">Toto pole obsahuje prvky z `array[0]` do `array[4]` .</span><span class="sxs-lookup"><span data-stu-id="a892e-106">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="a892e-107">Prvky pole jsou inicializovány na výchozí hodnotu typu prvku `0` pro celá čísla.</span><span class="sxs-lookup"><span data-stu-id="a892e-107">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="a892e-108">Pole mohou ukládat jakýkoli typ prvku, který zadáte, například následující příklad, který deklaruje pole řetězců:</span><span class="sxs-lookup"><span data-stu-id="a892e-108">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="a892e-109">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="a892e-109">Array Initialization</span></span>

<span data-ttu-id="a892e-110">Při deklaraci pole můžete inicializovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="a892e-110">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="a892e-111">Specifikátor délky není potřebný, protože je odvozený podle počtu prvků v inicializačním seznamu.</span><span class="sxs-lookup"><span data-stu-id="a892e-111">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="a892e-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a892e-112">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="a892e-113">Následující kód ukazuje deklaraci pole řetězců, kde je každý element pole inicializován pomocí názvu dne:</span><span class="sxs-lookup"><span data-stu-id="a892e-113">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="a892e-114">Můžete se vyhnout `new` výrazu a typu pole při inicializaci pole při deklaraci, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a892e-114">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="a892e-115">Toto se nazývá [implicitně typované pole](implicitly-typed-arrays.md):</span><span class="sxs-lookup"><span data-stu-id="a892e-115">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="a892e-116">Můžete deklarovat proměnnou pole bez jejího vytvoření, ale je nutné použít `new` operátor, pokud k této proměnné přiřadíte nové pole.</span><span class="sxs-lookup"><span data-stu-id="a892e-116">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="a892e-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a892e-117">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="a892e-118">Pole Typ hodnoty a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="a892e-118">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="a892e-119">Zvažte následující deklaraci pole:</span><span class="sxs-lookup"><span data-stu-id="a892e-119">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="a892e-120">Výsledek tohoto příkazu závisí na tom, zda `SomeType` je typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="a892e-120">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="a892e-121">Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="a892e-121">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="a892e-122">Pokud `SomeType` je odkazový typ, příkaz vytvoří pole 10 prvků, z nichž každá je inicializována na odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a892e-122">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="a892e-123">V obou instancích jsou prvky inicializovány na výchozí hodnotu pro typ prvku.</span><span class="sxs-lookup"><span data-stu-id="a892e-123">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="a892e-124">Další informace o typech hodnot a odkazových typech naleznete v tématu [typy hodnot](../../language-reference/builtin-types/value-types.md) a [odkazové typy](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a892e-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a892e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a892e-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="a892e-126">Pole</span><span class="sxs-lookup"><span data-stu-id="a892e-126">Arrays</span></span>](./index.md)
- [<span data-ttu-id="a892e-127">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="a892e-127">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="a892e-128">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="a892e-128">Jagged Arrays</span></span>](./jagged-arrays.md)
