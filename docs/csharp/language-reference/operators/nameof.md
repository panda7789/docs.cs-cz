---
title: výraz nameof – Referenční dokumentace jazyka C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: b00c5f6f97d27290fb3773dcbb422bf9fb4c425b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916779"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="d15c1-102">nameof – výraz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d15c1-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="d15c1-103">`nameof`Výraz vytvoří název proměnné, typu nebo členu jako řetězcové konstanty:</span><span class="sxs-lookup"><span data-stu-id="d15c1-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="d15c1-104">Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="d15c1-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="d15c1-105">V případě [doslovnéch identifikátorů](../tokens/verbatim.md)není `@` znak součástí názvu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="d15c1-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="d15c1-106">`nameof`Výraz je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="d15c1-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="d15c1-107">Výraz lze použít `nameof` k zajištění udržovatelnosti kódu kontroly argumentu:</span><span class="sxs-lookup"><span data-stu-id="d15c1-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="d15c1-108">`nameof`Výraz je k dispozici v C# 6 a novějším.</span><span class="sxs-lookup"><span data-stu-id="d15c1-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d15c1-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d15c1-109">C# language specification</span></span>

<span data-ttu-id="d15c1-110">Další informace naleznete v části [Expressions nameof](~/_csharplang/spec/expressions.md#nameof-expressions) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d15c1-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d15c1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d15c1-111">See also</span></span>

- [<span data-ttu-id="d15c1-112">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="d15c1-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d15c1-113">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="d15c1-113">C# operators and expressions</span></span>](index.md)
