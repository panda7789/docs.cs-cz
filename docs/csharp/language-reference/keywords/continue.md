---
title: Continue – příkaz C# – reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 74d166dbcf03b868baf464864e4c246f789df9cc
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605868"
---
# <a name="continue-c-reference"></a><span data-ttu-id="9b1ed-102">continue (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9b1ed-102">continue (C# Reference)</span></span>

<span data-ttu-id="9b1ed-103">[](./while.md) [](./do.md) [](./foreach-in.md) [](./for.md)Příkaz předá řízení následující iteraci ohraničujícího příkazu while, do, pro nebo foreach, ve kterém se zobrazí. `continue`</span><span class="sxs-lookup"><span data-stu-id="9b1ed-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="9b1ed-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b1ed-104">Example</span></span>

<span data-ttu-id="9b1ed-105">V tomto příkladu je čítač inicializován pro počítání od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="9b1ed-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="9b1ed-106">Pomocí `continue` příkazu v kombinaci s výrazem `(i < 9)`se přeskočí příkazy mezi `continue` a koncem `for` těla.</span><span class="sxs-lookup"><span data-stu-id="9b1ed-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="9b1ed-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b1ed-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9b1ed-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b1ed-108">See also</span></span>

- [<span data-ttu-id="9b1ed-109">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="9b1ed-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9b1ed-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9b1ed-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9b1ed-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b1ed-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9b1ed-112">break – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b1ed-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
