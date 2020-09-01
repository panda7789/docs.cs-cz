---
description: Continue – příkaz – reference jazyka C#
title: Continue – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128436"
---
# <a name="continue-c-reference"></a><span data-ttu-id="7e390-103">continue (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7e390-103">continue (C# Reference)</span></span>

<span data-ttu-id="7e390-104">`continue`Příkaz předá řízení následující iteraci ohraničujícího příkazu [while](./while.md), do [,](./do.md) [pro](./for.md)nebo [foreach](./foreach-in.md) , ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="7e390-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="7e390-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e390-105">Example</span></span>

<span data-ttu-id="7e390-106">V tomto příkladu je čítač inicializován pro počítání od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="7e390-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="7e390-107">Pomocí `continue` příkazu v kombinaci s výrazem `(i < 9)` `continue` se přeskočí příkazy mezi a koncem `for` těla.</span><span class="sxs-lookup"><span data-stu-id="7e390-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="7e390-108">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e390-108">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7e390-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e390-109">See also</span></span>

- [<span data-ttu-id="7e390-110">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e390-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7e390-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="7e390-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7e390-112">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e390-112">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="7e390-113">break – příkaz</span><span class="sxs-lookup"><span data-stu-id="7e390-113">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
