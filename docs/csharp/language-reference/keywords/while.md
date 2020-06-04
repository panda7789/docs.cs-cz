---
title: v jazyce C# – referenční informace
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: af616c2381b993f86296cbfa43a01ba2f9e000c2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401859"
---
# <a name="while-c-reference"></a><span data-ttu-id="15541-102">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="15541-102">while (C# Reference)</span></span>

<span data-ttu-id="15541-103">`while`Příkaz provede příkaz nebo blok příkazů, zatímco se zadaný logický výraz vyhodnotí jako `true` .</span><span class="sxs-lookup"><span data-stu-id="15541-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="15541-104">Vzhledem k tomu, že tento výraz je vyhodnocen před každým spuštěním smyčky, `while` smyčka se provede nula nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="15541-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="15541-105">To se liší [od smyčky do, která se spouští](do.md) jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="15541-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="15541-106">V jakémkoli bodě `while` bloku příkazu můžete přerušit smyčku pomocí příkazu [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="15541-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="15541-107">Můžete přímo Krokovat s vyhodnocením `while` výrazu pomocí příkazu [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="15541-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="15541-108">Pokud se výraz vyhodnotí jako `true` , vykonání pokračuje v prvním příkazu smyčky.</span><span class="sxs-lookup"><span data-stu-id="15541-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="15541-109">V opačném případě spuštění pokračuje v prvním příkazu za smyčkou.</span><span class="sxs-lookup"><span data-stu-id="15541-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="15541-110">Můžete také ukončit `while` smyčku příkazy [goto](goto.md), [return](return.md)nebo [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="15541-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="15541-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="15541-111">Example</span></span>

<span data-ttu-id="15541-112">Následující příklad ukazuje použití `while` příkazu.</span><span class="sxs-lookup"><span data-stu-id="15541-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="15541-113">Vyberte **Spustit** a spusťte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="15541-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="15541-114">Potom můžete kód upravit a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="15541-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="15541-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15541-115">C# language specification</span></span>

<span data-ttu-id="15541-116">Další informace naleznete v části [while](~/_csharplang/spec/statements.md#the-while-statement) v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="15541-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="15541-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="15541-117">See also</span></span>

- [<span data-ttu-id="15541-118">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15541-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="15541-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="15541-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="15541-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15541-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="15541-121">do – příkaz</span><span class="sxs-lookup"><span data-stu-id="15541-121">do statement</span></span>](do.md)
