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
ms.openlocfilehash: bfc997631cc147bf5718ec91a57e2995cead052f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236762"
---
# <a name="goto-c-reference"></a><span data-ttu-id="9a078-102">goto – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9a078-102">goto (C# Reference)</span></span>

<span data-ttu-id="9a078-103">`goto` Příkaz předá řízení programu přímo na označený příkaz.</span><span class="sxs-lookup"><span data-stu-id="9a078-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="9a078-104">Běžně `goto` je řízení je převedeno na konkrétní popisek případu přepínače nebo výchozí popisek v `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a078-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="9a078-105">`goto` Příkaz je také užitečné využít hluboce vnořený smyčky.</span><span class="sxs-lookup"><span data-stu-id="9a078-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="9a078-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a078-106">Example</span></span>

<span data-ttu-id="9a078-107">Následující příklad ukazuje použití `goto` v [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a078-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="9a078-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a078-108">Example</span></span>

<span data-ttu-id="9a078-109">Následující příklad ukazuje použití `goto` rozdělit z vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="9a078-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="9a078-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a078-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9a078-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a078-111">See also</span></span>

- [<span data-ttu-id="9a078-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a078-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="9a078-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a078-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="9a078-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a078-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="9a078-115">goto – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="9a078-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="9a078-116">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="9a078-116">Jump Statements</span></span>](jump-statements.md)  
