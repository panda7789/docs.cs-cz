---
title: New – omezení (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 9948fc65030a4636c5d23db4ef8c3a584018d2f5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087008"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="aba4c-102">New – omezení (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aba4c-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="aba4c-103">`new` Omezení určuje, že každý argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="aba4c-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="aba4c-104">Typ omezení new použít, nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="aba4c-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="aba4c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aba4c-105">Example</span></span>

<span data-ttu-id="aba4c-106">Použít `new` omezení parametru typu, když obecné třídy vytvoří nové instance daného typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aba4c-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="aba4c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="aba4c-107">Example</span></span>

<span data-ttu-id="aba4c-108">Při použití `new()` omezení s jinými omezeními, musí se zadat poslední:</span><span class="sxs-lookup"><span data-stu-id="aba4c-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="aba4c-109">Další informace najdete v tématu [omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aba4c-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aba4c-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aba4c-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aba4c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aba4c-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="aba4c-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aba4c-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="aba4c-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="aba4c-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aba4c-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aba4c-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="aba4c-115">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="aba4c-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="aba4c-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="aba4c-116">Generics</span></span>](../../programming-guide/generics/index.md)