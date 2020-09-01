---
description: break – příkaz – reference jazyka C#
title: break – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134741"
---
# <a name="break-c-reference"></a><span data-ttu-id="a9e26-103">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a9e26-103">break (C# Reference)</span></span>

<span data-ttu-id="a9e26-104">`break`Příkaz ukončí nejbližší ohraničující smyčku nebo příkaz [Switch](./switch.md) , ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a9e26-104">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="a9e26-105">Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="a9e26-105">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="a9e26-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9e26-106">Example</span></span>

<span data-ttu-id="a9e26-107">V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; `break` příkaz však ukončí smyčku po 4 počtech.</span><span class="sxs-lookup"><span data-stu-id="a9e26-107">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="a9e26-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9e26-108">Example</span></span>

<span data-ttu-id="a9e26-109">Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="a9e26-109">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="a9e26-110">Pokud jste zadali `4` , bude výstup:</span><span class="sxs-lookup"><span data-stu-id="a9e26-110">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="a9e26-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9e26-111">Example</span></span>

<span data-ttu-id="a9e26-112">V tomto příkladu `break` je příkaz použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce.</span><span class="sxs-lookup"><span data-stu-id="a9e26-112">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="a9e26-113">Řízení je vráceno _pouze_ ve vnořených smyčkách o jednu úroveň výš.</span><span class="sxs-lookup"><span data-stu-id="a9e26-113">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="a9e26-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9e26-114">Example</span></span>

<span data-ttu-id="a9e26-115">V tomto příkladu `break` je příkaz použit pouze k přerušení aktuální větve během každé iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="a9e26-115">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="a9e26-116">Samotný cyklus není ovlivněn instancemi `break` , které patří do vnořeného příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="a9e26-116">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="a9e26-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9e26-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a9e26-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9e26-118">See also</span></span>

- [<span data-ttu-id="a9e26-119">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9e26-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a9e26-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a9e26-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a9e26-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9e26-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="a9e26-122">přepnutí</span><span class="sxs-lookup"><span data-stu-id="a9e26-122">switch</span></span>](./switch.md)
