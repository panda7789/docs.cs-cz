---
title: "do (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords: do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a><span data-ttu-id="2fe73-102">do (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2fe73-102">do (C# Reference)</span></span>
<span data-ttu-id="2fe73-103">`do` Příkaz spustí příkaz nebo blok příkazů opakovaně dokud vyhodnotí zadaný výraz pro `false`.</span><span class="sxs-lookup"><span data-stu-id="2fe73-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="2fe73-104">V závorkách, musí být uzavřena do těla smyčky `{}`, pokud se skládá z jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="2fe73-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="2fe73-105">V takovém případě jsou volitelné složené závorky.</span><span class="sxs-lookup"><span data-stu-id="2fe73-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fe73-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fe73-106">Example</span></span>  
 <span data-ttu-id="2fe73-107">V následujícím příkladu `do-while` smyčky příkazy spustit stejně dlouho jako proměnnou `x` je menší než 5.</span><span class="sxs-lookup"><span data-stu-id="2fe73-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="2fe73-108">Na rozdíl od [při](../../../csharp/language-reference/keywords/while.md) příkaz, `do-while` smyčky se spustí jednou předtím, než je vyhodnocena podmíněným výrazem.</span><span class="sxs-lookup"><span data-stu-id="2fe73-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="2fe73-109">Na kterémkoli bodu v `do-while` bloku, může dojít k narušení mimo pomocí smyčky [zalomení](../../../csharp/language-reference/keywords/break.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="2fe73-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="2fe73-110">Můžete přímo na krok `while` příkaz vyhodnocení výrazu pomocí [pokračovat](../../../csharp/language-reference/keywords/continue.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="2fe73-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="2fe73-111">Pokud `while` výraz vyhodnocen jako true, provádění pokračuje první příkaz ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="2fe73-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="2fe73-112">Pokud je výsledkem na hodnotu false, pokračuje první příkaz po spuštění `do-while` smyčky.</span><span class="sxs-lookup"><span data-stu-id="2fe73-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="2fe73-113">A `do-while` smyčky můžete také měly být byl ukončen ve [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="2fe73-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2fe73-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fe73-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2fe73-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fe73-115">See Also</span></span>  
 [<span data-ttu-id="2fe73-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fe73-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2fe73-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2fe73-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2fe73-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fe73-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2fe73-119">Proveďte-while – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="2fe73-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="2fe73-120">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="2fe73-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
