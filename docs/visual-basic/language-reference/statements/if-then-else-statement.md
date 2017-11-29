---
title: "If...Then...Else – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="e9dfe-102">If...Then...Else – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9dfe-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="e9dfe-103">Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9dfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9dfe-104">Syntax</span></span>  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e9dfe-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e9dfe-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="e9dfe-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-106">Required.</span></span> <span data-ttu-id="e9dfe-107">Výraz.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-107">Expression.</span></span> <span data-ttu-id="e9dfe-108">Se musí vyhodnotit `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-108">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="e9dfe-109">Pokud je ve výrazu [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), podmínka je zpracován jako výraz není `True`a `Else` blok je spustit.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-109">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is not `True`, and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="e9dfe-110">Požadované v jednom řádku syntaxi; volitelné v syntaxi více řádků.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-110">Required in the single-line syntax; optional in the multiple-line syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="e9dfe-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-111">Optional.</span></span> <span data-ttu-id="e9dfe-112">Jeden nebo více následujících příkazů `If`... `Then` které jsou spouštěny, pokud `condition` vyhodnocuje `True`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-112">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="e9dfe-113">Požadováno pokud `ElseIf` je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-113">Required if `ElseIf` is present.</span></span> <span data-ttu-id="e9dfe-114">Výraz.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-114">Expression.</span></span> <span data-ttu-id="e9dfe-115">Se musí vyhodnotit `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-115">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="e9dfe-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-116">Optional.</span></span> <span data-ttu-id="e9dfe-117">Jeden nebo více následujících příkazů `ElseIf`... `Then` které jsou spouštěny, pokud `elseifcondition` vyhodnocuje `True`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-117">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="e9dfe-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-118">Optional.</span></span> <span data-ttu-id="e9dfe-119">Jeden nebo více příkazů, které jsou spouštěny, pokud žádné předchozí `condition` nebo `elseifcondition` výraz vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-119">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="e9dfe-120">Ukončí `If`... `Then`... `Else` bloku.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-120">Terminates the `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9dfe-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9dfe-121">Remarks</span></span>  
  
## <a name="multiple-line-syntax"></a><span data-ttu-id="e9dfe-122">Syntaxe více řádků</span><span class="sxs-lookup"><span data-stu-id="e9dfe-122">Multiple-Line Syntax</span></span>  
 <span data-ttu-id="e9dfe-123">Když `If`... `Then`... `Else` příkaz je zjistil, `condition` testování.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-123">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="e9dfe-124">Pokud `condition` je `True`, následující příkazy `Then` provedení.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-124">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="e9dfe-125">Pokud `condition` je `False`, každý `ElseIf` (pokud existují) vyhodnotí v pořadí.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-125">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="e9dfe-126">Když `True``elseifcondition` nenajde, příkazy hned za přidruženého `ElseIf` provedení.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-126">When a `True``elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="e9dfe-127">Pokud žádné `elseifcondition` vyhodnotí jako `True`, nebo pokud nejsou žádné `ElseIf` příkazy, následující příkazy `Else` provedení.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-127">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="e9dfe-128">Po provedení následující příkazy `Then`, `ElseIf`, nebo `Else`, provádění pokračuje následující příkaz `End If`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-128">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="e9dfe-129">`ElseIf` a `Else` klauzule jsou obě volitelné.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-129">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="e9dfe-130">Může mít jako mnoho `ElseIf` klauzule jako je vhodné `If`... `Then`... `Else` příkaz, ale ne `ElseIf` klauzule může vyskytovat po `Else` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-130">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="e9dfe-131">`If`... `Then`... `Else` příkazy můžete začlenit do jiné.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-131">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="e9dfe-132">V syntaxi více řádků `If` příkaz musí být jediným příkazem v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-132">In the multiple-line syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="e9dfe-133">`ElseIf`, `Else`, A `End If` příkazy lze předcházet pouze čáry popisku.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-133">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="e9dfe-134">`If`... `Then`... `Else` bloku musí končit `End If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-134">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="e9dfe-135">[Vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnotit jeden výraz, který má několik možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-135">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
## <a name="single-line-syntax"></a><span data-ttu-id="e9dfe-136">Syntaxe jednoho řádku</span><span class="sxs-lookup"><span data-stu-id="e9dfe-136">Single-Line Syntax</span></span>  
 <span data-ttu-id="e9dfe-137">Pomocí syntaxe jeden řádek pro krátké, jednoduché testy.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-137">You can use the single-line syntax for short, simple tests.</span></span> <span data-ttu-id="e9dfe-138">Syntaxe více řádků však poskytuje další strukturu a flexibilitu a je obvykle jednodušší pro čtení, údržbu a ladění.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-138">However, the multiple-line syntax provides more structure and flexibility and is usually easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="e9dfe-139">Jaké způsobem `Then` – klíčové slovo je prověřit, abyste zjistili, zda příkaz je jeden řádek `If`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-139">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="e9dfe-140">Pokud jakoukoli jinou hodnotu než komentář se zobrazí po `Then` na stejném řádku příkaz považován za jeden řádek `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-140">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="e9dfe-141">Pokud `Then` chybí, musí být spuštění více řádků `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-141">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="e9dfe-142">V syntaxi jeden řádek, může mít více příkazů provést v důsledku `If`... `Then` rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-142">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="e9dfe-143">Všechny příkazy musí být na stejném řádku a být oddělené dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-143">All statements must be on the same line and be separated by colons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9dfe-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9dfe-144">Example</span></span>  
 <span data-ttu-id="e9dfe-145">Následující příklad ukazuje použití syntaxe více řádků `If`... `Then`... `Else` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-145">The following example illustrates the use of the multiple-line syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e9dfe-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9dfe-146">Example</span></span>  
 <span data-ttu-id="e9dfe-147">Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-147">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="e9dfe-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9dfe-148">Example</span></span>  
 <span data-ttu-id="e9dfe-149">Následující příklad ukazuje použití syntaxe jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="e9dfe-149">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9dfe-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9dfe-150">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="e9dfe-151">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="e9dfe-151">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="e9dfe-152">Vyberte... Case – příkaz</span><span class="sxs-lookup"><span data-stu-id="e9dfe-152">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="e9dfe-153">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="e9dfe-153">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="e9dfe-154">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="e9dfe-154">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="e9dfe-155">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9dfe-155">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="e9dfe-156">Pokud operátor</span><span class="sxs-lookup"><span data-stu-id="e9dfe-156">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
