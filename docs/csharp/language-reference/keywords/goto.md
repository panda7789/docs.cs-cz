---
title: příkaz goto - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: e4642d0e43a538217493298b58d572e435db5dae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645324"
---
# <a name="goto-c-reference"></a><span data-ttu-id="6abe7-102">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6abe7-102">goto (C# Reference)</span></span>

<span data-ttu-id="6abe7-103">`goto` Příkaz předá řízení programu přímo na označený příkaz.</span><span class="sxs-lookup"><span data-stu-id="6abe7-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="6abe7-104">Běžně `goto` je řízení je převedeno na konkrétní popisek případu přepínače nebo výchozí popisek v `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6abe7-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="6abe7-105">`goto` Příkaz je také užitečné využít hluboce vnořený smyčky.</span><span class="sxs-lookup"><span data-stu-id="6abe7-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="6abe7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6abe7-106">Example</span></span>

<span data-ttu-id="6abe7-107">Následující příklad ukazuje použití `goto` v [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="6abe7-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="6abe7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6abe7-108">Example</span></span>

<span data-ttu-id="6abe7-109">Následující příklad ukazuje použití `goto` rozdělit z vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="6abe7-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="6abe7-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6abe7-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6abe7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6abe7-111">See also</span></span>

- [<span data-ttu-id="6abe7-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6abe7-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6abe7-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6abe7-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6abe7-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6abe7-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6abe7-115">goto – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="6abe7-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
- [<span data-ttu-id="6abe7-116">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="6abe7-116">Jump Statements</span></span>](jump-statements.md)
