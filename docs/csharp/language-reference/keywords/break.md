---
title: BREAK – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 987ee1ca5601b3dd105412bf0fa18361c57a95fd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315235"
---
# <a name="break-c-reference"></a><span data-ttu-id="b5873-102">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b5873-102">break (C# Reference)</span></span>

<span data-ttu-id="b5873-103">`break` Příkaz ukončí nejbližší nadřazených smyčky nebo [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b5873-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="b5873-104">Ovládací prvek předává do příkazu, který následuje ukončenou příkaz, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="b5873-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="b5873-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5873-105">Example</span></span>

<span data-ttu-id="b5873-106">V tomto příkladu obsahuje příkaz podmíněného čítač, který by měl počítat od 1 do 100; ale `break` příkaz ukončí smyčky po 4 počty.</span><span class="sxs-lookup"><span data-stu-id="b5873-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="b5873-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5873-107">Example</span></span>

<span data-ttu-id="b5873-108">V tomto příkladu `break` se použije příkaz k přerušení mimo smyčky vnořené vnitřní a vnější smyčky vrácení řízení.</span><span class="sxs-lookup"><span data-stu-id="b5873-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="b5873-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5873-109">Example</span></span>

<span data-ttu-id="b5873-110">Tento příklad ukazuje použití `break` v [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="b5873-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="b5873-111">Pokud jste zadali `4`, bude výstup:</span><span class="sxs-lookup"><span data-stu-id="b5873-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="b5873-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5873-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b5873-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5873-113">See Also</span></span>

[<span data-ttu-id="b5873-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5873-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="b5873-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b5873-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="b5873-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5873-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="b5873-117">switch</span><span class="sxs-lookup"><span data-stu-id="b5873-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
[<span data-ttu-id="b5873-118">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="b5873-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
[<span data-ttu-id="b5873-119">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="b5873-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
