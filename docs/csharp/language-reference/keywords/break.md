---
title: příkaz break – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713755"
---
# <a name="break-c-reference"></a><span data-ttu-id="3e105-102">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3e105-102">break (C# Reference)</span></span>

<span data-ttu-id="3e105-103">Příkaz `break` ukončí nejbližší ohraničující smyčku nebo příkaz [Switch](./switch.md) , ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="3e105-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="3e105-104">Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="3e105-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="3e105-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e105-105">Example</span></span>

<span data-ttu-id="3e105-106">V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; příkaz `break` však ukončí smyčku po 4 počtech.</span><span class="sxs-lookup"><span data-stu-id="3e105-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="3e105-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e105-107">Example</span></span>

<span data-ttu-id="3e105-108">Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="3e105-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="3e105-109">Pokud jste zadali `4`, výstup by byl:</span><span class="sxs-lookup"><span data-stu-id="3e105-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="3e105-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e105-110">Example</span></span>

<span data-ttu-id="3e105-111">V tomto příkladu je příkaz `break` použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce.</span><span class="sxs-lookup"><span data-stu-id="3e105-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="3e105-112">Řízení je vráceno _pouze_ ve vnořených smyčkách o jednu úroveň výš.</span><span class="sxs-lookup"><span data-stu-id="3e105-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="3e105-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e105-113">Example</span></span>

<span data-ttu-id="3e105-114">V tomto příkladu je příkaz `break` použit pouze k přerušení aktuální větve během každé iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="3e105-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="3e105-115">Samotný cyklus není ovlivněn instancemi `break`, které patří do vnořeného příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="3e105-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="3e105-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e105-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3e105-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e105-117">See also</span></span>

- [<span data-ttu-id="3e105-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="3e105-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3e105-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3e105-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3e105-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e105-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3e105-121">switch</span><span class="sxs-lookup"><span data-stu-id="3e105-121">switch</span></span>](./switch.md)
