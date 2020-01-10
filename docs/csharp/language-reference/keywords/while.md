---
title: while C# – referenční informace
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: eb9aa2ea8d6b1c96e0be7d377f7c047194b598de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712790"
---
# <a name="while-c-reference"></a><span data-ttu-id="c675d-102">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c675d-102">while (C# Reference)</span></span>

<span data-ttu-id="c675d-103">Příkaz `while` spustí příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="c675d-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="c675d-104">Vzhledem k tomu, že tento výraz je vyhodnocen před každým spuštěním smyčky, `while` smyčka provede nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="c675d-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="c675d-105">To se liší [od smyčky do, která se spouští](do.md) jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="c675d-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="c675d-106">V jakémkoli okamžiku v rámci bloku příkazu `while` lze rozdělit smyčku pomocí příkazu [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="c675d-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="c675d-107">Můžete krokovat přímo s vyhodnocením výrazu `while` pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="c675d-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c675d-108">Pokud se výraz vyhodnotí jako `true`, vykonání pokračuje v prvním příkazu smyčky.</span><span class="sxs-lookup"><span data-stu-id="c675d-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="c675d-109">V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.</span><span class="sxs-lookup"><span data-stu-id="c675d-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="c675d-110">Můžete také ukončit `while` smyčkou příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="c675d-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="c675d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c675d-111">Example</span></span>

<span data-ttu-id="c675d-112">Následující příklad ukazuje použití příkazu `while`.</span><span class="sxs-lookup"><span data-stu-id="c675d-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="c675d-113">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="c675d-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="c675d-114">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="c675d-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="c675d-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c675d-115">C# language specification</span></span>

<span data-ttu-id="c675d-116">Další informace naleznete v oddílu [while](~/_csharplang/spec/statements.md#the-while-statement) v tématu [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c675d-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c675d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c675d-117">See also</span></span>

- [<span data-ttu-id="c675d-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="c675d-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c675d-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c675d-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c675d-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c675d-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c675d-121">do – příkaz</span><span class="sxs-lookup"><span data-stu-id="c675d-121">do statement</span></span>](do.md)
