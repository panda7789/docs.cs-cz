---
title: do (Referenční dokumentace jazyka C#)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4dd5f4034bcd60b714071eb7eb9518e66ac0c848
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129022"
---
# <a name="do-c-reference"></a><span data-ttu-id="db35f-102">do (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="db35f-102">do (C# Reference)</span></span>

<span data-ttu-id="db35f-103">`do` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="db35f-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="db35f-104">Vzhledem k tomu, že tento výraz je vyhodnocen po každém spuštění smyčky, `do-while` cyklus se opakuje, jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="db35f-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="db35f-105">Tím se liší od [při](while.md) smyčku, která spustí nulakrát nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="db35f-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="db35f-106">Na libovolný bod v rámci `do` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="db35f-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="db35f-107">Přejdete přímo na vyhodnocení `while` výrazem s použitím [pokračovat](continue.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="db35f-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="db35f-108">Pokud je výraz vyhodnocen `true`, běh programu pokračuje prvním příkazem ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="db35f-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="db35f-109">V opačném případě běh programu pokračuje prvním příkazem za smyčky.</span><span class="sxs-lookup"><span data-stu-id="db35f-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="db35f-110">Také můžete ukončit `do-while` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="db35f-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="db35f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="db35f-111">Example</span></span>

<span data-ttu-id="db35f-112">Následující příklad ukazuje použití `do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="db35f-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="db35f-113">Vyberte **spustit** ke spuštění příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="db35f-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="db35f-114">Potom můžete upravit kód a potom ho spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="db35f-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="db35f-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="db35f-115">C# language specification</span></span>

<span data-ttu-id="db35f-116">Další informace najdete v tématu [proveďte příkaz](~/_csharplang/spec/statements.md#the-do-statement) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="db35f-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db35f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db35f-117">See also</span></span>

- [<span data-ttu-id="db35f-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="db35f-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="db35f-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="db35f-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="db35f-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="db35f-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="db35f-121">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="db35f-121">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="db35f-122">while – příkaz</span><span class="sxs-lookup"><span data-stu-id="db35f-122">while statement</span></span>](while.md)
