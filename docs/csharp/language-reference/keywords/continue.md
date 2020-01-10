---
title: Continue – příkaz C# – reference
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713663"
---
# <a name="continue-c-reference"></a><span data-ttu-id="2af58-102">continue (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2af58-102">continue (C# Reference)</span></span>

<span data-ttu-id="2af58-103">Příkaz `continue` předá řízení další iteraci ohraničujícího příkazu [while](./while.md) [, do,](./do.md) [pro](./for.md)nebo [foreach](./foreach-in.md) , ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2af58-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="2af58-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2af58-104">Example</span></span>

<span data-ttu-id="2af58-105">V tomto příkladu je čítač inicializován pro počítání od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="2af58-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="2af58-106">Pomocí příkazu `continue` ve spojení s `(i < 9)`výrazů se příkazy mezi `continue` a koncem `for`ho textu přeskočí.</span><span class="sxs-lookup"><span data-stu-id="2af58-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="2af58-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2af58-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2af58-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2af58-108">See also</span></span>

- [<span data-ttu-id="2af58-109">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="2af58-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2af58-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2af58-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2af58-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2af58-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2af58-112">break – příkaz</span><span class="sxs-lookup"><span data-stu-id="2af58-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
