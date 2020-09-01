---
description: goto – příkaz – reference jazyka C#
title: goto – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128423"
---
# <a name="goto-c-reference"></a><span data-ttu-id="a45bd-103">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a45bd-103">goto (C# Reference)</span></span>

<span data-ttu-id="a45bd-104">`goto`Příkaz přenáší ovládací prvek program přímo na označený příkaz.</span><span class="sxs-lookup"><span data-stu-id="a45bd-104">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="a45bd-105">Běžné použití aplikace `goto` je pro přenos řízení na konkrétní návěští přepínače Case nebo jako výchozí popisek v `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a45bd-105">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="a45bd-106">`goto`Příkaz je také užitečný pro získání nehluboce vnořených smyček.</span><span class="sxs-lookup"><span data-stu-id="a45bd-106">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="a45bd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a45bd-107">Example</span></span>

<span data-ttu-id="a45bd-108">Následující příklad ukazuje použití `goto` příkazu v příkazu [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="a45bd-108">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="a45bd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a45bd-109">Example</span></span>

<span data-ttu-id="a45bd-110">Následující příklad ukazuje použití `goto` k přerušení z vnořených smyček.</span><span class="sxs-lookup"><span data-stu-id="a45bd-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="a45bd-111">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a45bd-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a45bd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a45bd-112">See also</span></span>

- [<span data-ttu-id="a45bd-113">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a45bd-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a45bd-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a45bd-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a45bd-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a45bd-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a45bd-116">goto – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="a45bd-116">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
