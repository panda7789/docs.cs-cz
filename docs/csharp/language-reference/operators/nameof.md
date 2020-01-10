---
title: operátor nameof – C# odkaz
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: c1d71d52a9222379adc36479715113b181da7133
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712686"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="63638-102">nameof – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="63638-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="63638-103">Operátor `nameof` Získá název proměnné, typu nebo členu jako řetězcové konstanty:</span><span class="sxs-lookup"><span data-stu-id="63638-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="63638-104">Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="63638-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="63638-105">Operátor `nameof` je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="63638-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="63638-106">Operátor `nameof` lze použít k zajištění udržovatelnosti kódu pro kontrolu argumentu:</span><span class="sxs-lookup"><span data-stu-id="63638-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="63638-107">Operátor `nameof` je k dispozici C# v 6 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="63638-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63638-108">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="63638-108">C# language specification</span></span>

<span data-ttu-id="63638-109">Další informace najdete v části [výrazy nameof](~/_csharplang/spec/expressions.md#nameof-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="63638-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63638-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63638-110">See also</span></span>

- [<span data-ttu-id="63638-111">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="63638-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="63638-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="63638-112">C# operators</span></span>](index.md)
