---
title: goto – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: d4fd9f1f26b82b409d704c45e4bcf18cceef8282
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405813"
---
# <a name="goto-c-reference"></a><span data-ttu-id="c1893-102">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c1893-102">goto (C# Reference)</span></span>

<span data-ttu-id="c1893-103">`goto` Příkaz předá řízení programu přímo na označený příkaz.</span><span class="sxs-lookup"><span data-stu-id="c1893-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="c1893-104">Běžně `goto` je řízení je převedeno na konkrétní popisek případu přepínače nebo výchozí popisek v `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c1893-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="c1893-105">`goto` Příkaz je také užitečné využít hluboce vnořený smyčky.</span><span class="sxs-lookup"><span data-stu-id="c1893-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="c1893-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1893-106">Example</span></span>

<span data-ttu-id="c1893-107">Následující příklad ukazuje použití `goto` v [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="c1893-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="c1893-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1893-108">Example</span></span>

<span data-ttu-id="c1893-109">Následující příklad ukazuje použití `goto` rozdělit z vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="c1893-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="c1893-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1893-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c1893-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1893-111">See also</span></span>

- [<span data-ttu-id="c1893-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1893-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="c1893-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c1893-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="c1893-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1893-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="c1893-115">goto – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="c1893-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="c1893-116">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="c1893-116">Jump Statements</span></span>](jump-statements.md)  
