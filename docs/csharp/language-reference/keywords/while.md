---
title: while - C# Reference
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 481d3f7b87dbe874de010825c3c7f052e4bc33c0
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738743"
---
# <a name="while-c-reference"></a><span data-ttu-id="bc540-102">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bc540-102">while (C# Reference)</span></span>

<span data-ttu-id="bc540-103">Příkaz `while` provede příkaz nebo blok příkazů, zatímco zadaný logický `true`výraz je vyhodnocen .</span><span class="sxs-lookup"><span data-stu-id="bc540-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="bc540-104">Vzhledem k tomu, že tento výraz `while` je vyhodnocenpřed každým spuštěním smyčky, smyčka provede nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="bc540-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="bc540-105">To se liší od [smyčky do,](do.md) která se provádí jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="bc540-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="bc540-106">V libovolném `while` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí příkazu [break.](break.md)</span><span class="sxs-lookup"><span data-stu-id="bc540-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="bc540-107">Můžete krok přímo k vyhodnocení `while` výrazu pomocí [příkazu continue.](continue.md)</span><span class="sxs-lookup"><span data-stu-id="bc540-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="bc540-108">Pokud výraz vyhodnotí `true`, spuštění pokračuje na první příkaz ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="bc540-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="bc540-109">V opačném případě provádění pokračuje na první příkaz po smyčky.</span><span class="sxs-lookup"><span data-stu-id="bc540-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="bc540-110">`while` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="bc540-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="bc540-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc540-111">Example</span></span>

<span data-ttu-id="bc540-112">Následující příklad ukazuje použití `while` příkazu.</span><span class="sxs-lookup"><span data-stu-id="bc540-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="bc540-113">Chcete-li spustit ukázkový kód, vyberte **spustit.**</span><span class="sxs-lookup"><span data-stu-id="bc540-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="bc540-114">Poté můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="bc540-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="bc540-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc540-115">C# language specification</span></span>

<span data-ttu-id="bc540-116">Další informace naleznete v části [While statement](~/_csharplang/spec/statements.md#the-while-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="bc540-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc540-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc540-117">See also</span></span>

- [<span data-ttu-id="bc540-118">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc540-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc540-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc540-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc540-120">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bc540-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bc540-121">do příkaz</span><span class="sxs-lookup"><span data-stu-id="bc540-121">do statement</span></span>](do.md)
