---
title: odkaz na C#
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 5612cfb2462117ac431de9c702cd8137f495e5dc
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551814"
---
# <a name="do-c-reference"></a><span data-ttu-id="7e2bc-102">do (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7e2bc-102">do (C# Reference)</span></span>

<span data-ttu-id="7e2bc-103">Příkaz `do` spustí příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="7e2bc-104">Vzhledem k tomu, že tento výraz je vyhodnocen po každém spuštění smyčky, spustí se `do-while` cyklus jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="7e2bc-105">To se liší od smyčky [while](while.md) , která se spouští nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="7e2bc-106">V jakémkoli okamžiku v rámci bloku příkazu `do` lze rozdělit smyčku pomocí příkazu [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="7e2bc-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="7e2bc-107">Můžete krokovat přímo s vyhodnocením výrazu `while` pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="7e2bc-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="7e2bc-108">Pokud se výraz vyhodnotí jako `true`, vykonání pokračuje v prvním příkazu smyčky.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="7e2bc-109">V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="7e2bc-110">Můžete také ukončit `do-while` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="7e2bc-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="7e2bc-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e2bc-111">Example</span></span>

<span data-ttu-id="7e2bc-112">Následující příklad ukazuje použití příkazu `do`.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="7e2bc-113">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="7e2bc-114">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="7e2bc-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="7e2bc-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e2bc-115">C# language specification</span></span>

<span data-ttu-id="7e2bc-116">Další informace naleznete v části do [příkazu](~/_csharplang/spec/statements.md#the-do-statement) do ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="7e2bc-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e2bc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e2bc-117">See also</span></span>

- [<span data-ttu-id="7e2bc-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="7e2bc-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7e2bc-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7e2bc-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7e2bc-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e2bc-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7e2bc-121">while – příkaz</span><span class="sxs-lookup"><span data-stu-id="7e2bc-121">while statement</span></span>](while.md)
