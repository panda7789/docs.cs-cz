---
title: goto – příkaz C# – reference
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715276"
---
# <a name="goto-c-reference"></a><span data-ttu-id="b334e-102">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b334e-102">goto (C# Reference)</span></span>

<span data-ttu-id="b334e-103">Příkaz `goto` přenáší ovládací prvek program přímo na označený příkaz.</span><span class="sxs-lookup"><span data-stu-id="b334e-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="b334e-104">Běžné použití `goto` je přenášet řízení na konkrétní popisek Case přepínače nebo výchozí popisek v příkazu `switch`.</span><span class="sxs-lookup"><span data-stu-id="b334e-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="b334e-105">Příkaz `goto` je také užitečný k získání z hluboce vnořených smyček.</span><span class="sxs-lookup"><span data-stu-id="b334e-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="b334e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b334e-106">Example</span></span>

<span data-ttu-id="b334e-107">Následující příklad ukazuje použití `goto` v příkazu [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="b334e-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="b334e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b334e-108">Example</span></span>

<span data-ttu-id="b334e-109">Následující příklad ukazuje použití `goto` k přerušení z vnořených smyček.</span><span class="sxs-lookup"><span data-stu-id="b334e-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="b334e-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b334e-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b334e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b334e-111">See also</span></span>

- [<span data-ttu-id="b334e-112">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b334e-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b334e-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b334e-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b334e-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b334e-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b334e-115">goto – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="b334e-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
