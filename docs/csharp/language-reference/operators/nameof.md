---
title: operátor nameof – C# odkaz
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: fa858db918cdaf04c757f2741265e359acb74f7b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036341"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="d2bef-102">nameof – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="d2bef-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="d2bef-103">Operátor `nameof` Získá název proměnné, typu nebo členu jako řetězcové konstanty:</span><span class="sxs-lookup"><span data-stu-id="d2bef-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="d2bef-104">Jak ukazuje předchozí příklad, v případě typu a oboru názvů není vytvořen název obvykle [plně kvalifikovaný](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="d2bef-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="d2bef-105">Operátor `nameof` je vyhodnocen v době kompilace a nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="d2bef-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="d2bef-106">Operátor `nameof` lze použít k zajištění udržovatelnosti kódu pro kontrolu argumentu:</span><span class="sxs-lookup"><span data-stu-id="d2bef-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="d2bef-107">Operátor `nameof` je k dispozici C# v 6 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="d2bef-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d2bef-108">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2bef-108">C# language specification</span></span>

<span data-ttu-id="d2bef-109">Další informace najdete v části [výrazy nameof](~/_csharplang/spec/expressions.md#nameof-expressions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d2bef-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2bef-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2bef-110">See also</span></span>

- [<span data-ttu-id="d2bef-111">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="d2bef-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d2bef-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2bef-112">C# operators</span></span>](index.md)
