---
title: nameof expression - C# odkaz
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507136"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="82926-102">nameof expression (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="82926-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="82926-103">Výraz `nameof` vytvoří název proměnné, typu nebo člena jako řetězcovou konstantu:</span><span class="sxs-lookup"><span data-stu-id="82926-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="82926-104">Jak ukazuje předchozí příklad, v případě typu a oboru názvů není produkovaný název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="82926-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="82926-105">Výraz `nameof` je vyhodnocován v době kompilace a nemá žádný vliv v době běhu.</span><span class="sxs-lookup"><span data-stu-id="82926-105">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="82926-106">Výraz můžete `nameof` použít k tomu, aby byl kód pro kontrolu argumentů více udržovatelný:</span><span class="sxs-lookup"><span data-stu-id="82926-106">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="82926-107">Výraz `nameof` je k dispozici v C# 6 a novější.</span><span class="sxs-lookup"><span data-stu-id="82926-107">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="82926-108">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="82926-108">C# language specification</span></span>

<span data-ttu-id="82926-109">Další informace naleznete v části [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="82926-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82926-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="82926-110">See also</span></span>

- [<span data-ttu-id="82926-111">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="82926-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="82926-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="82926-112">C# operators</span></span>](index.md)
