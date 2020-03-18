---
title: příkaz break - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713755"
---
# <a name="break-c-reference"></a><span data-ttu-id="d123b-102">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d123b-102">break (C# Reference)</span></span>

<span data-ttu-id="d123b-103">Příkaz `break` ukončí nejbližší ohraničující smyčky nebo [switch](./switch.md) příkaz, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d123b-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="d123b-104">Ovládací prvek je předán příkazu, který následuje za ukončené prohlášení, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="d123b-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="d123b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d123b-105">Example</span></span>

<span data-ttu-id="d123b-106">V tomto příkladu podmíněné prohlášení obsahuje čítač, který má počítat od 1 do 100; však `break` příkaz ukončí smyčky po 4 počítá.</span><span class="sxs-lookup"><span data-stu-id="d123b-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="d123b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d123b-107">Example</span></span>

<span data-ttu-id="d123b-108">Tento příklad ukazuje použití `break` v [příkazu switch.](./switch.md)</span><span class="sxs-lookup"><span data-stu-id="d123b-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="d123b-109">Pokud jste `4`zadali , výstup by byl:</span><span class="sxs-lookup"><span data-stu-id="d123b-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="d123b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d123b-110">Example</span></span>

<span data-ttu-id="d123b-111">V tomto příkladu `break` se příkaz používá k přerušení vnitřní vnořené smyčky a vrácení ovládacího prvku do vnější smyčky.</span><span class="sxs-lookup"><span data-stu-id="d123b-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="d123b-112">Ovládací prvek je _vrácena pouze_ o jednu úroveň výš v vnořené smyčky.</span><span class="sxs-lookup"><span data-stu-id="d123b-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="d123b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="d123b-113">Example</span></span>

<span data-ttu-id="d123b-114">V tomto příkladu `break` se příkaz používá pouze k přerušení aktuální větve během každé iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="d123b-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="d123b-115">Samotná smyčka není ovlivněna `break` instancemi, které patří do vnořeného [příkazu switch.](./switch.md)</span><span class="sxs-lookup"><span data-stu-id="d123b-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="d123b-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d123b-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d123b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d123b-117">See also</span></span>

- [<span data-ttu-id="d123b-118">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d123b-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d123b-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d123b-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d123b-120">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d123b-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d123b-121">Přepnout</span><span class="sxs-lookup"><span data-stu-id="d123b-121">switch</span></span>](./switch.md)
