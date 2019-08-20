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
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602244"
---
# <a name="break-c-reference"></a><span data-ttu-id="45cee-102">break (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="45cee-102">break (C# Reference)</span></span>

<span data-ttu-id="45cee-103">Příkaz ukončí nejbližší ohraničující smyčku nebo příkaz switch, ve kterém se zobrazí. [](./switch.md) `break`</span><span class="sxs-lookup"><span data-stu-id="45cee-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="45cee-104">Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="45cee-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="45cee-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="45cee-105">Example</span></span>

<span data-ttu-id="45cee-106">V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; `break` příkaz však ukončí smyčku po 4 počtech.</span><span class="sxs-lookup"><span data-stu-id="45cee-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="45cee-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="45cee-107">Example</span></span>

<span data-ttu-id="45cee-108">V tomto příkladu `break` je příkaz použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce.</span><span class="sxs-lookup"><span data-stu-id="45cee-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="45cee-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="45cee-109">Example</span></span>

<span data-ttu-id="45cee-110">Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="45cee-110">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="45cee-111">Pokud jste zadali `4`, bude výstup:</span><span class="sxs-lookup"><span data-stu-id="45cee-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="45cee-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45cee-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="45cee-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45cee-113">See also</span></span>

- [<span data-ttu-id="45cee-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="45cee-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45cee-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="45cee-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45cee-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45cee-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="45cee-117">switch</span><span class="sxs-lookup"><span data-stu-id="45cee-117">switch</span></span>](./switch.md)
