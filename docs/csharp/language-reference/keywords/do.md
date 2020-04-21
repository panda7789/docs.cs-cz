---
title: do - C# Odkaz
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738910"
---
# <a name="do-c-reference"></a><span data-ttu-id="a7a1e-102">do (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a7a1e-102">do (C# Reference)</span></span>

<span data-ttu-id="a7a1e-103">Příkaz `do` provede příkaz nebo blok příkazů, zatímco zadaný logický `true`výraz je vyhodnocen .</span><span class="sxs-lookup"><span data-stu-id="a7a1e-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="a7a1e-104">Vzhledem k tomu, že tento výraz `do-while` je vyhodnocena po každém spuštění smyčky, smyčky provede jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="a7a1e-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="a7a1e-105">To se liší od [while](while.md) smyčky, která provádí nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="a7a1e-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="a7a1e-106">V libovolném `do` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí příkazu [break.](break.md)</span><span class="sxs-lookup"><span data-stu-id="a7a1e-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="a7a1e-107">Můžete krok přímo k vyhodnocení `while` výrazu pomocí [příkazu continue.](continue.md)</span><span class="sxs-lookup"><span data-stu-id="a7a1e-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="a7a1e-108">Pokud výraz vyhodnotí `true`, spuštění pokračuje na první příkaz ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="a7a1e-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="a7a1e-109">V opačném případě provádění pokračuje na první příkaz po smyčky.</span><span class="sxs-lookup"><span data-stu-id="a7a1e-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="a7a1e-110">`do-while` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="a7a1e-110">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="a7a1e-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7a1e-111">Example</span></span>

<span data-ttu-id="a7a1e-112">Následující příklad ukazuje použití `do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a7a1e-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="a7a1e-113">Chcete-li spustit ukázkový kód, vyberte **spustit.**</span><span class="sxs-lookup"><span data-stu-id="a7a1e-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="a7a1e-114">Poté můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="a7a1e-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="a7a1e-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7a1e-115">C# language specification</span></span>

<span data-ttu-id="a7a1e-116">Další informace naleznete v části [do prohlášení](~/_csharplang/spec/statements.md#the-do-statement) specifikace jazyka [C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a7a1e-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7a1e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7a1e-117">See also</span></span>

- [<span data-ttu-id="a7a1e-118">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7a1e-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a7a1e-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7a1e-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a7a1e-120">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a7a1e-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a7a1e-121">zatímco příkaz</span><span class="sxs-lookup"><span data-stu-id="a7a1e-121">while statement</span></span>](while.md)
