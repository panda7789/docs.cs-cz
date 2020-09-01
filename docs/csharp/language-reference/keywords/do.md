---
description: do – reference jazyka C#
title: do – reference jazyka C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 601231f23a58e8af8339a733677f0bbd92bb4ffc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126954"
---
# <a name="do-c-reference"></a><span data-ttu-id="b2e70-103">do (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b2e70-103">do (C# Reference)</span></span>

<span data-ttu-id="b2e70-104">`do`Příkaz provede příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true` .</span><span class="sxs-lookup"><span data-stu-id="b2e70-104">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="b2e70-105">Vzhledem k tomu, že tento výraz je vyhodnocen po každém spuštění smyčky, `do-while` smyčka se spustí jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="b2e70-105">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="b2e70-106">To se liší od smyčky [while](while.md) , která se spouští nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="b2e70-106">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="b2e70-107">V jakémkoli bodě `do` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="b2e70-107">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="b2e70-108">Můžete přímo Krokovat s vyhodnocením `while` výrazu pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="b2e70-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="b2e70-109">Pokud se výraz vyhodnotí jako `true` , vykonání pokračuje v prvním příkazu smyčky.</span><span class="sxs-lookup"><span data-stu-id="b2e70-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="b2e70-110">V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.</span><span class="sxs-lookup"><span data-stu-id="b2e70-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="b2e70-111">Můžete také ukončit `do-while` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="b2e70-111">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="b2e70-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2e70-112">Example</span></span>

<span data-ttu-id="b2e70-113">Následující příklad ukazuje použití `do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b2e70-113">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="b2e70-114">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="b2e70-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="b2e70-115">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="b2e70-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="b2e70-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2e70-116">C# language specification</span></span>

<span data-ttu-id="b2e70-117">Další informace naleznete v části do [příkazu](~/_csharplang/spec/statements.md#the-do-statement) do v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b2e70-117">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2e70-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2e70-118">See also</span></span>

- [<span data-ttu-id="b2e70-119">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2e70-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b2e70-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b2e70-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b2e70-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2e70-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b2e70-122">while – příkaz</span><span class="sxs-lookup"><span data-stu-id="b2e70-122">while statement</span></span>](while.md)
