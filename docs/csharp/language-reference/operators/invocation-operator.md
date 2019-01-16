---
title: () – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 656a1ca7a992df43ff857d2c4ecb62b044f7e06f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333275"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6765d-102">() – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="6765d-102">() operator (C# Reference)</span></span>

<span data-ttu-id="6765d-103">Kromě používá k určení pořadí operací ve výrazu závorky slouží k provádění následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="6765d-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>

1. <span data-ttu-id="6765d-104">Zadejte přetypování a převody typů.</span><span class="sxs-lookup"><span data-stu-id="6765d-104">Specify casts, or type conversions.</span></span>

    [!code-csharp[csRefOperators#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#1)]

2. <span data-ttu-id="6765d-105">Vyvolání metod a delegátů.</span><span class="sxs-lookup"><span data-stu-id="6765d-105">Invoke methods or delegates.</span></span>

    [!code-csharp[csRefOperators#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#2)]

## <a name="remarks"></a><span data-ttu-id="6765d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6765d-106">Remarks</span></span>

<span data-ttu-id="6765d-107">Přetypování vyvolá explicitní operátor převodu z jednoho typu na jiný; přetypování selže, pokud není definován žádný převod operátor.</span><span class="sxs-lookup"><span data-stu-id="6765d-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="6765d-108">Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../keywords/explicit.md) a [implicitní](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="6765d-108">To define a conversion operator, see [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md).</span></span>

 <span data-ttu-id="6765d-109">`()` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="6765d-109">The `()` operator cannot be overloaded.</span></span>

 <span data-ttu-id="6765d-110">Další informace najdete v tématu [přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="6765d-110">For more information, see [Casting and Type Conversions](../../programming-guide/types/casting-and-type-conversions.md).</span></span>

 <span data-ttu-id="6765d-111">Další informace o volání metody, naleznete v tématu [metody](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="6765d-111">For more information about method invocation, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6765d-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6765d-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6765d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6765d-113">See also</span></span>

- [<span data-ttu-id="6765d-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6765d-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6765d-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6765d-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6765d-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6765d-116">C# Operators</span></span>](index.md)