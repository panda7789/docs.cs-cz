---
title: If...Then...Else – příkaz (Visual Basic)
ms.date: 04/16/2018
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
ms.openlocfilehash: d91a913d515f36a6b974850bc30079b000a919b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842691"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="3ddda-102">If...Then...Else – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ddda-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="3ddda-103">Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.</span><span class="sxs-lookup"><span data-stu-id="3ddda-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddda-104">Syntax</span></span>  
  
```  
' Multiline syntax:  
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="3ddda-105">Rychlé odkazy na ukázkový kód</span><span class="sxs-lookup"><span data-stu-id="3ddda-105">Quick links to example code</span></span>

<span data-ttu-id="3ddda-106">Tento článek obsahuje několik příkladů, které ilustrují použití `If`... `Then`... `Else` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="3ddda-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

* [<span data-ttu-id="3ddda-107">Příklad víceřádkové syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddda-107">Multiline syntax example</span></span>](#multi-line)
* [<span data-ttu-id="3ddda-108">Příklad vnořené syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddda-108">Nested syntax example</span></span>](#nested)
* [<span data-ttu-id="3ddda-109">Příklad syntaxe jedním řádkem</span><span class="sxs-lookup"><span data-stu-id="3ddda-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="3ddda-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="3ddda-110">Parts</span></span>  
 `condition`  
 <span data-ttu-id="3ddda-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3ddda-111">Required.</span></span> <span data-ttu-id="3ddda-112">výraz.</span><span class="sxs-lookup"><span data-stu-id="3ddda-112">Expression.</span></span> <span data-ttu-id="3ddda-113">Musí být vyhodnocen `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="3ddda-114">Pokud má výraz hodnotu [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která se vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), podmínka je zpracováván stejně, jako je výraz `False` a `Else` je blok proveden.</span><span class="sxs-lookup"><span data-stu-id="3ddda-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False` and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="3ddda-115">Vyžaduje v syntaxi jedním řádkem; nepovinné v syntaxi víceřádkový.</span><span class="sxs-lookup"><span data-stu-id="3ddda-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="3ddda-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3ddda-116">Optional.</span></span> <span data-ttu-id="3ddda-117">Jeden nebo více následujících příkazů `If`... `Then` , která se spustí, pokud `condition` vyhodnotí jako `True`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="3ddda-118">Požadováno pokud `ElseIf` je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3ddda-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="3ddda-119">výraz.</span><span class="sxs-lookup"><span data-stu-id="3ddda-119">Expression.</span></span> <span data-ttu-id="3ddda-120">Musí být vyhodnocen `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="3ddda-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3ddda-121">Optional.</span></span> <span data-ttu-id="3ddda-122">Jeden nebo více následujících příkazů `ElseIf`... `Then` , která se spustí, pokud `elseifcondition` vyhodnotí jako `True`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="3ddda-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3ddda-123">Optional.</span></span> <span data-ttu-id="3ddda-124">Jeden nebo více příkazů, které jsou spouštěny, pokud žádné předchozí `condition` nebo `elseifcondition` výraz vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="3ddda-125">Ukončí víceřádkové verzi `If`... `Then`... `Else` bloku.</span><span class="sxs-lookup"><span data-stu-id="3ddda-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ddda-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ddda-126">Remarks</span></span>  
  
### <a name="multiline-syntax"></a><span data-ttu-id="3ddda-127">Multiline – syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddda-127">Multiline syntax</span></span>  
 <span data-ttu-id="3ddda-128">Když `If`... `Then`... `Else` příkazu nalezen, `condition` je testován.</span><span class="sxs-lookup"><span data-stu-id="3ddda-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="3ddda-129">Pokud `condition` je `True`, příkazy po `Then` provádějí.</span><span class="sxs-lookup"><span data-stu-id="3ddda-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="3ddda-130">Pokud `condition` je `False`každá `ElseIf` – příkaz (Pokud tam nějaké jsou) se vyhodnocuje podle pořadí.</span><span class="sxs-lookup"><span data-stu-id="3ddda-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="3ddda-131">Když `True` `elseifcondition` se nachází bezprostředně následující přidružené příkazy `ElseIf` provádějí.</span><span class="sxs-lookup"><span data-stu-id="3ddda-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="3ddda-132">Pokud ne `elseifcondition` vyhodnotí jako `True`, nebo pokud nejsou žádné `ElseIf` příkazy, příkazy po `Else` provádějí.</span><span class="sxs-lookup"><span data-stu-id="3ddda-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="3ddda-133">Po provedení následující příkazy `Then`, `ElseIf`, nebo `Else`, pokračuje se příkaz následující `End If`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="3ddda-134">`ElseIf` a `Else` klauzule jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="3ddda-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="3ddda-135">Můžete mít kolik `ElseIf` klauzulí je vhodné `If`... `Then`... `Else` příkazu, ale ne `ElseIf` klauzule může být po `Else` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3ddda-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="3ddda-136">`If`... `Then`... `Else` příkazy mohou být vnořené do jiné.</span><span class="sxs-lookup"><span data-stu-id="3ddda-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="3ddda-137">Víceřádkový syntaxe `If` příkaz musí být jediným příkazem v prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="3ddda-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="3ddda-138">`ElseIf`, `Else`, A `End If` příkazy nesmí následovat pouze po popisku řádku.</span><span class="sxs-lookup"><span data-stu-id="3ddda-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="3ddda-139">`If`... `Then`... `Else` bloku musí končit `End If` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3ddda-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="3ddda-140">[Vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnotíte jediný výraz, který má několik možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="3ddda-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
### <a name="single-line-syntax"></a><span data-ttu-id="3ddda-141">Syntaxe jednoho řádku</span><span class="sxs-lookup"><span data-stu-id="3ddda-141">Single-Line syntax</span></span>  
 <span data-ttu-id="3ddda-142">Syntaxe jedním řádkem pro jednu podmínku s kódem můžete spustit, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="3ddda-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="3ddda-143">Více řádků syntaxe však poskytuje další struktury a flexibilitu a je jednodušší pro čtení, spravovat a ladit.</span><span class="sxs-lookup"><span data-stu-id="3ddda-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="3ddda-144">Jaké způsobem `Then` – klíčové slovo je prověřit, abyste zjistili, zda je příkaz jedním řádkem `If`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="3ddda-145">Pokud nic jiného než komentář se zobrazí po `Then` na stejném řádku, příkaz je považován za jeden řádek `If` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3ddda-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="3ddda-146">Pokud `Then` chybí, musí být začátek řádku více `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="3ddda-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="3ddda-147">V syntaxi jedním řádkem, může mít více příkazů provést, protože výsledek `If`... `Then` rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="3ddda-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="3ddda-148">Všechny příkazy se musí nacházet na stejném řádku a být odděleny dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="3ddda-148">All statements must be on the same line and be separated by colons.</span></span>  

## <a name="multiline-syntax-example"></a><span data-ttu-id="3ddda-149">Příklad víceřádkové syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddda-149">Multiline syntax example</span></span>

<a name="multi-line"></a>
 
 <span data-ttu-id="3ddda-150">Následující příklad ukazuje použití víceřádkové syntaxe `If`... `Then`... `Else` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3ddda-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="3ddda-151">Příklad vnořené syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddda-151">Nested syntax example</span></span>

<a name="nested"></a>

 <span data-ttu-id="3ddda-152">Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3ddda-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="3ddda-153">Příklad syntaxe jedním řádkem</span><span class="sxs-lookup"><span data-stu-id="3ddda-153">Single-Line syntax example</span></span>
  
<a name="single-line"></a> <span data-ttu-id="3ddda-154">Následující příklad ukazuje použití syntaxe jedním řádkem.</span><span class="sxs-lookup"><span data-stu-id="3ddda-154">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a><span data-ttu-id="3ddda-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ddda-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="3ddda-156">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="3ddda-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="3ddda-157">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="3ddda-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="3ddda-158">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="3ddda-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="3ddda-159">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="3ddda-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="3ddda-160">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ddda-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="3ddda-161">Operátor If</span><span class="sxs-lookup"><span data-stu-id="3ddda-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
