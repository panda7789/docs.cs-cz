---
title: příkaz break – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 2628da73364cf94a52e2862d349243c100d4afaf
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179938"
---
# <a name="break-c-reference"></a><span data-ttu-id="4f073-102">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4f073-102">break (C# Reference)</span></span>

<span data-ttu-id="4f073-103">Příkaz `break` ukončí nejbližší ohraničující smyčku nebo příkaz [Switch](./switch.md) , ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="4f073-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="4f073-104">Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="4f073-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="4f073-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f073-105">Example</span></span>

<span data-ttu-id="4f073-106">V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; příkaz `break` však ukončí smyčku po 4 počtech.</span><span class="sxs-lookup"><span data-stu-id="4f073-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="4f073-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f073-107">Example</span></span>

<span data-ttu-id="4f073-108">Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="4f073-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="4f073-109">Pokud jste zadali `4`, výstup by byl:</span><span class="sxs-lookup"><span data-stu-id="4f073-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="4f073-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f073-110">Example</span></span>

<span data-ttu-id="4f073-111">V tomto příkladu je příkaz `break` použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce.</span><span class="sxs-lookup"><span data-stu-id="4f073-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="4f073-112">Řízení je vráceno _pouze_ ve vnořených smyčkách o jednu úroveň výš.</span><span class="sxs-lookup"><span data-stu-id="4f073-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="4f073-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f073-113">Example</span></span>

<span data-ttu-id="4f073-114">V tomto příkladu se příkaz `break` používá pouze k přerušení aktuální větve během každé iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="4f073-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="4f073-115">Samotný cyklus není ovlivněn instancemi `break`, které patří do vnořeného příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="4f073-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="4f073-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4f073-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4f073-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f073-117">See also</span></span>

- [<span data-ttu-id="4f073-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="4f073-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4f073-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4f073-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4f073-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4f073-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4f073-121">switch</span><span class="sxs-lookup"><span data-stu-id="4f073-121">switch</span></span>](./switch.md)
