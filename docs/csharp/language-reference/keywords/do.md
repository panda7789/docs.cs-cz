---
title: do (Referenční dokumentace jazyka C#)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 89c13f5b547c13052e229ff6eb3a39ae5babce41
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932384"
---
# <a name="do-c-reference"></a><span data-ttu-id="60cf3-102">do (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="60cf3-102">do (C# Reference)</span></span>

<span data-ttu-id="60cf3-103">`do` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="60cf3-103">The `do` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="60cf3-104">Vzhledem k tomu, že tento výraz je vyhodnocen po každém spuštění smyčky, `do-while` cyklus se opakuje, jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="60cf3-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="60cf3-105">Tím se liší od [při](while.md) smyčku, která spustí nulakrát nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="60cf3-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="60cf3-106">Na libovolný bod v rámci `do` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="60cf3-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="60cf3-107">Přejdete přímo na vyhodnocení `while` výrazem s použitím [pokračovat](continue.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="60cf3-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="60cf3-108">Pokud je výraz vyhodnocen `true`, běh programu pokračuje prvním příkazem ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="60cf3-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="60cf3-109">V opačném případě běh programu pokračuje prvním příkazem za smyčky.</span><span class="sxs-lookup"><span data-stu-id="60cf3-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="60cf3-110">Také můžete ukončit `do-while` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="60cf3-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="60cf3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="60cf3-111">Example</span></span>

<span data-ttu-id="60cf3-112">Následující příklad ukazuje použití `do` příkazu.</span><span class="sxs-lookup"><span data-stu-id="60cf3-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="60cf3-113">Vyberte **spustit** ke spuštění příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="60cf3-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="60cf3-114">Potom můžete upravit kód a potom ho spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="60cf3-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="60cf3-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60cf3-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="60cf3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60cf3-116">See also</span></span>

- [<span data-ttu-id="60cf3-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60cf3-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="60cf3-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="60cf3-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="60cf3-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60cf3-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="60cf3-120">do-while – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="60cf3-120">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
- [<span data-ttu-id="60cf3-121">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="60cf3-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="60cf3-122">while – příkaz</span><span class="sxs-lookup"><span data-stu-id="60cf3-122">while statement</span></span>](while.md)  
