---
title: while (Referenční dokumentace jazyka C#)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: e3e9493b5371fbd6f53a779ba73743efc6d6e05b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514057"
---
# <a name="while-c-reference"></a><span data-ttu-id="383c5-102">while (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="383c5-102">while (C# Reference)</span></span>

<span data-ttu-id="383c5-103">`while` Příkaz opakuje příkaz nebo blok příkazů během zadaný logický výraz je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="383c5-103">The `while` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="383c5-104">Vzhledem k tomu, že tento výraz je vyhodnocen před každým provedením smyčky, `while` cyklus se opakuje nulakrát nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="383c5-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="383c5-105">Tím se liší od [proveďte](do.md) smyčku, která spustí jednou nebo vícekrát.</span><span class="sxs-lookup"><span data-stu-id="383c5-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="383c5-106">Na libovolný bod v rámci `while` blok příkazů, můžete přerušit ze smyčky s použitím [přerušení](break.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="383c5-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="383c5-107">Přejdete přímo na vyhodnocení `while` výrazem s použitím [pokračovat](continue.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="383c5-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="383c5-108">Pokud je výraz vyhodnocen `true`, běh programu pokračuje prvním příkazem ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="383c5-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="383c5-109">V opačném případě běh programu pokračuje prvním příkazem za smyčky.</span><span class="sxs-lookup"><span data-stu-id="383c5-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="383c5-110">Také můžete ukončit `while` smyčky pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="383c5-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="383c5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="383c5-111">Example</span></span>

<span data-ttu-id="383c5-112">Následující příklad ukazuje použití `while` příkazu.</span><span class="sxs-lookup"><span data-stu-id="383c5-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="383c5-113">Vyberte **spustit** ke spuštění příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="383c5-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="383c5-114">Potom můžete upravit kód a potom ho spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="383c5-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="383c5-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="383c5-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="383c5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="383c5-116">See also</span></span>

- [<span data-ttu-id="383c5-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="383c5-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="383c5-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="383c5-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="383c5-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="383c5-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="383c5-120">while – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="383c5-120">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
- [<span data-ttu-id="383c5-121">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="383c5-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="383c5-122">do – příkaz</span><span class="sxs-lookup"><span data-stu-id="383c5-122">do statement</span></span>](do.md)  
