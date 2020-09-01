---
description: v jazyce C# – referenční informace
title: v jazyce C# – referenční informace
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 97299f9ac6f2cdd6bbddf831b3ee2ad711935fbe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141865"
---
# <a name="while-c-reference"></a><span data-ttu-id="88ceb-103">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="88ceb-103">while (C# Reference)</span></span>

<span data-ttu-id="88ceb-104">`while`Příkaz provede příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true` .</span><span class="sxs-lookup"><span data-stu-id="88ceb-104">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="88ceb-105">Vzhledem k tomu, že tento výraz je vyhodnocen před každým spuštěním smyčky, `while` smyčka se provede nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="88ceb-105">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="88ceb-106">To se liší [od smyčky do, která se spouští](do.md) jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="88ceb-106">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="88ceb-107">V jakémkoli bodě `while` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="88ceb-107">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="88ceb-108">Můžete přímo Krokovat s vyhodnocením `while` výrazu pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="88ceb-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="88ceb-109">Pokud se výraz vyhodnotí jako `true` , vykonání pokračuje v prvním příkazu smyčky.</span><span class="sxs-lookup"><span data-stu-id="88ceb-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="88ceb-110">V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.</span><span class="sxs-lookup"><span data-stu-id="88ceb-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="88ceb-111">Můžete také ukončit `while` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="88ceb-111">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="88ceb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="88ceb-112">Example</span></span>

<span data-ttu-id="88ceb-113">Následující příklad ukazuje použití `while` příkazu.</span><span class="sxs-lookup"><span data-stu-id="88ceb-113">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="88ceb-114">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="88ceb-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="88ceb-115">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="88ceb-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="88ceb-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88ceb-116">C# language specification</span></span>

<span data-ttu-id="88ceb-117">Další informace naleznete v části [while](~/_csharplang/spec/statements.md#the-while-statement) v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="88ceb-117">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="88ceb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="88ceb-118">See also</span></span>

- [<span data-ttu-id="88ceb-119">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88ceb-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="88ceb-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="88ceb-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="88ceb-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88ceb-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="88ceb-122">do – příkaz</span><span class="sxs-lookup"><span data-stu-id="88ceb-122">do statement</span></span>](do.md)
