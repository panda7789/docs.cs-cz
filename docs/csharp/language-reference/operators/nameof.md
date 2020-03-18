---
title: nameof operátor - c# odkaz
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846269"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="03209-102">nameof operátor (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="03209-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="03209-103">Operátor `nameof` získá název proměnné, typu nebo člena jako řetězcovou konstantu:</span><span class="sxs-lookup"><span data-stu-id="03209-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="03209-104">Jak ukazuje předchozí příklad, v případě typu a oboru názvů není produkovaný název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="03209-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="03209-105">Operátor `nameof` je vyhodnocován v době kompilace a nemá žádný vliv v době běhu.</span><span class="sxs-lookup"><span data-stu-id="03209-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="03209-106">Pomocí operátoru `nameof` můžete vytvořit kód pro kontrolu argumentů, který bude moci být udržovatelný:</span><span class="sxs-lookup"><span data-stu-id="03209-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="03209-107">Operátor `nameof` je k dispozici v C# 6 a novější.</span><span class="sxs-lookup"><span data-stu-id="03209-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03209-108">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03209-108">C# language specification</span></span>

<span data-ttu-id="03209-109">Další informace naleznete v části [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="03209-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03209-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="03209-110">See also</span></span>

- [<span data-ttu-id="03209-111">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="03209-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="03209-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03209-112">C# operators</span></span>](index.md)
