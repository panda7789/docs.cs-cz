---
title: příkaz goto - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715276"
---
# <a name="goto-c-reference"></a><span data-ttu-id="13da2-102">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="13da2-102">goto (C# Reference)</span></span>

<span data-ttu-id="13da2-103">Příkaz `goto` přenese ovládací prvek programu přímo do popiskovaného příkazu.</span><span class="sxs-lookup"><span data-stu-id="13da2-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="13da2-104">Běžné použití `goto` je převést řízení na konkrétní popisek switch-case `switch` nebo výchozí popisek v příkazu.</span><span class="sxs-lookup"><span data-stu-id="13da2-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="13da2-105">Příkaz `goto` je také užitečné se dostat z hluboce vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="13da2-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="13da2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="13da2-106">Example</span></span>

<span data-ttu-id="13da2-107">Následující příklad ukazuje `goto` použití v [příkazu switch.](switch.md)</span><span class="sxs-lookup"><span data-stu-id="13da2-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="13da2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="13da2-108">Example</span></span>

<span data-ttu-id="13da2-109">Následující příklad ukazuje `goto` použití vymanit se z vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="13da2-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="13da2-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13da2-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="13da2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="13da2-111">See also</span></span>

- [<span data-ttu-id="13da2-112">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13da2-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13da2-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13da2-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13da2-114">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="13da2-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="13da2-115">goto – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="13da2-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
