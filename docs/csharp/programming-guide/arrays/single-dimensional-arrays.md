---
title: Jednorozměrná pole – Průvodce programováním v C#
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: e189253eedc21fa2d51e16407f04b034610bb57b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410241"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="1b6f0-102">Jednorozměrná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1b6f0-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1b6f0-103">Vytvoříte jednorozměrné pole pomocí operátoru [New](../../language-reference/operators/new-operator.md) , který určuje typ prvku pole a počet prvků.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-103">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="1b6f0-104">Následující příklad deklaruje pole pěti celých čísel:</span><span class="sxs-lookup"><span data-stu-id="1b6f0-104">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="1b6f0-105">Toto pole obsahuje prvky z `array[0]` do `array[4]` .</span><span class="sxs-lookup"><span data-stu-id="1b6f0-105">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="1b6f0-106">Prvky pole jsou inicializovány na výchozí hodnotu typu prvku `0` pro celá čísla.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-106">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="1b6f0-107">Pole mohou ukládat jakýkoli typ prvku, který zadáte, například následující příklad, který deklaruje pole řetězců:</span><span class="sxs-lookup"><span data-stu-id="1b6f0-107">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="1b6f0-108">Inicializace pole</span><span class="sxs-lookup"><span data-stu-id="1b6f0-108">Array Initialization</span></span>

<span data-ttu-id="1b6f0-109">Při deklaraci pole můžete inicializovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-109">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="1b6f0-110">Specifikátor délky není potřebný, protože je odvozený podle počtu prvků v inicializačním seznamu.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-110">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="1b6f0-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1b6f0-111">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="1b6f0-112">Následující kód ukazuje deklaraci pole řetězců, kde je každý element pole inicializován pomocí názvu dne:</span><span class="sxs-lookup"><span data-stu-id="1b6f0-112">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="1b6f0-113">Můžete se vyhnout `new` výrazu a typu pole při inicializaci pole při deklaraci, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-113">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="1b6f0-114">Toto se nazývá [implicitně typované pole](implicitly-typed-arrays.md):</span><span class="sxs-lookup"><span data-stu-id="1b6f0-114">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="1b6f0-115">Můžete deklarovat proměnnou pole bez jejího vytvoření, ale je nutné použít `new` operátor, pokud k této proměnné přiřadíte nové pole.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-115">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="1b6f0-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1b6f0-116">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="1b6f0-117">Pole Typ hodnoty a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="1b6f0-117">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="1b6f0-118">Zvažte následující deklaraci pole:</span><span class="sxs-lookup"><span data-stu-id="1b6f0-118">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="1b6f0-119">Výsledek tohoto příkazu závisí na tom, zda `SomeType` je typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-119">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="1b6f0-120">Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="1b6f0-120">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="1b6f0-121">Pokud `SomeType` je odkazový typ, příkaz vytvoří pole 10 prvků, z nichž každá je inicializována na odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-121">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="1b6f0-122">V obou instancích jsou prvky inicializovány na výchozí hodnotu pro typ prvku.</span><span class="sxs-lookup"><span data-stu-id="1b6f0-122">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="1b6f0-123">Další informace o typech hodnot a odkazových typech naleznete v tématu [typy hodnot](../../language-reference/builtin-types/value-types.md) a [odkazové typy](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1b6f0-123">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1b6f0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b6f0-124">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="1b6f0-125">Pole</span><span class="sxs-lookup"><span data-stu-id="1b6f0-125">Arrays</span></span>](./index.md)
- [<span data-ttu-id="1b6f0-126">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="1b6f0-126">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="1b6f0-127">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="1b6f0-127">Jagged Arrays</span></span>](./jagged-arrays.md)
