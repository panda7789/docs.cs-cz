---
title: operátor nameof - C# odkaz
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 945a8a8ff6d96cb505fa10e85c21a93347661a23
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238690"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="cb9f4-102">operátor nameof (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="cb9f4-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="cb9f4-103">`nameof` Operátor získá název proměnné, typ nebo člena jako řetězcová konstanta:</span><span class="sxs-lookup"><span data-stu-id="cb9f4-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="cb9f4-104">Jak ukazuje předchozí příklad, v případě typu a obor názvů, název vyprodukované není obvykle [úplný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="cb9f4-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="cb9f4-105">`nameof` Operátor je vyhodnocen v době kompilace a nemá žádný vliv za běhu.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-105">The `nameof` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="cb9f4-106">Můžete použít `nameof` operátor provádět jednodušší údržbu argument Kontrola kódu:</span><span class="sxs-lookup"><span data-stu-id="cb9f4-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="cb9f4-107">`nameof` Operátor je k dispozici v C# 6 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="cb9f4-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cb9f4-108">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cb9f4-108">C# language specification</span></span>

<span data-ttu-id="cb9f4-109">Další informace najdete v tématu [výrazy Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f4-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb9f4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb9f4-110">See also</span></span>

- [<span data-ttu-id="cb9f4-111">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="cb9f4-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cb9f4-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cb9f4-112">C# operators</span></span>](index.md)
