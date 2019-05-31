---
title: while – C# odkaz
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 486936ae29552891c6a58913b6d5cf9a0d725a69
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422493"
---
# <a name="while-c-reference"></a><span data-ttu-id="de3a5-102">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="de3a5-102">while (C# Reference)</span></span>

<span data-ttu-id="de3a5-103">`while` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="de3a5-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="de3a5-104">Vzhledem k tomu, že tento výraz je vyhodnocen před každým provedením smyčky, `while` cyklus se opakuje nulakrát nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="de3a5-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="de3a5-105">Tím se liší od [proveďte](do.md) smyčku, která spustí jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="de3a5-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="de3a5-106">Na libovolný bod v rámci `while` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="de3a5-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="de3a5-107">Přejdete přímo na vyhodnocení `while` výrazem s použitím [pokračovat](continue.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="de3a5-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="de3a5-108">Pokud je výraz vyhodnocen `true`, běh programu pokračuje prvním příkazem ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="de3a5-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="de3a5-109">V opačném případě běh programu pokračuje prvním příkazem za smyčky.</span><span class="sxs-lookup"><span data-stu-id="de3a5-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="de3a5-110">Také můžete ukončit `while` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="de3a5-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="de3a5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="de3a5-111">Example</span></span>

<span data-ttu-id="de3a5-112">Následující příklad ukazuje použití `while` příkazu.</span><span class="sxs-lookup"><span data-stu-id="de3a5-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="de3a5-113">Vyberte **spustit** ke spuštění příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="de3a5-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="de3a5-114">Potom můžete upravit kód a potom ho spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="de3a5-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="de3a5-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="de3a5-115">C# language specification</span></span>

<span data-ttu-id="de3a5-116">Další informace najdete v tématu [while – příkaz](~/_csharplang/spec/statements.md#the-while-statement) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="de3a5-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de3a5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de3a5-117">See also</span></span>

- [<span data-ttu-id="de3a5-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="de3a5-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="de3a5-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="de3a5-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="de3a5-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="de3a5-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="de3a5-121">do – příkaz</span><span class="sxs-lookup"><span data-stu-id="de3a5-121">do statement</span></span>](do.md)
