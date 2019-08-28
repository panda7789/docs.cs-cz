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
ms.openlocfilehash: 97ac8c82df14eb5ddc5e26fdaddf61cc774a0476
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046572"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="a1b84-102">If...Then...Else – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1b84-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="a1b84-103">Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.</span><span class="sxs-lookup"><span data-stu-id="a1b84-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1b84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-104">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="a1b84-105">Rychlé odkazy na příklad kódu</span><span class="sxs-lookup"><span data-stu-id="a1b84-105">Quick links to example code</span></span>

<span data-ttu-id="a1b84-106">Tento článek obsahuje několik příkladů, které ilustrují použití `If`... `Then`... `Else` příkaz:</span><span class="sxs-lookup"><span data-stu-id="a1b84-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

* [<span data-ttu-id="a1b84-107">Příklad víceřádkové syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-107">Multiline syntax example</span></span>](#multi-line)
* [<span data-ttu-id="a1b84-108">Příklad vnořené syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-108">Nested syntax example</span></span>](#nested)
* [<span data-ttu-id="a1b84-109">Příklad syntaxe s jedním řádkem</span><span class="sxs-lookup"><span data-stu-id="a1b84-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="a1b84-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="a1b84-110">Parts</span></span>

`condition` \
<span data-ttu-id="a1b84-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a1b84-111">Required.</span></span> <span data-ttu-id="a1b84-112">Vyjádření.</span><span class="sxs-lookup"><span data-stu-id="a1b84-112">Expression.</span></span> <span data-ttu-id="a1b84-113">Je nutné vyhodnotit na `True` nebo `False`, nebo na datový typ, který je implicitně převoditelný na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a1b84-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="a1b84-114">Pokud je výraz proměnnou s [možnou hodnotou null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , která je vyhodnocena jako [Nothing](../../../visual-basic/language-reference/nothing.md), je podmínka považována `False` za, `Else` Pokud je výraz a je proveden blok.</span><span class="sxs-lookup"><span data-stu-id="a1b84-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False` and the `Else` block is executed.</span></span>

`Then` \
<span data-ttu-id="a1b84-115">Vyžadované v syntaxi na jednom řádku; volitelné v syntaxi na více řádků.</span><span class="sxs-lookup"><span data-stu-id="a1b84-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="a1b84-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a1b84-116">Optional.</span></span> <span data-ttu-id="a1b84-117">Jeden nebo více příkazů, `If`které následují... , které se spustí `condition` , pokud je `True`vyhodnoceno jako. `Then`</span><span class="sxs-lookup"><span data-stu-id="a1b84-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="a1b84-118">Požadováno, `ElseIf` Pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a1b84-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="a1b84-119">Vyjádření.</span><span class="sxs-lookup"><span data-stu-id="a1b84-119">Expression.</span></span> <span data-ttu-id="a1b84-120">Je nutné vyhodnotit na `True` nebo `False`, nebo na datový typ, který je implicitně převoditelný na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a1b84-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="a1b84-121">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a1b84-121">Optional.</span></span> <span data-ttu-id="a1b84-122">Jeden nebo více příkazů, `ElseIf`které následují... , které se spustí `elseifcondition` , pokud je `True`vyhodnoceno jako. `Then`</span><span class="sxs-lookup"><span data-stu-id="a1b84-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="a1b84-123">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a1b84-123">Optional.</span></span> <span data-ttu-id="a1b84-124">Jeden nebo více příkazů, které jsou spuštěny, `condition` Pokud `elseifcondition` žádný předchozí nebo výraz `True`není vyhodnocen jako.</span><span class="sxs-lookup"><span data-stu-id="a1b84-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="a1b84-125">Ukončí víceřádkovou verzi `If`... `Then`... `Else` blok.</span><span class="sxs-lookup"><span data-stu-id="a1b84-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1b84-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1b84-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="a1b84-127">Víceřádková syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-127">Multiline syntax</span></span>

<span data-ttu-id="a1b84-128">`If`Když... `Then`... byl zjištěn příkaz, `condition` je testován. `Else`</span><span class="sxs-lookup"><span data-stu-id="a1b84-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="a1b84-129">V případě `condition`,jsou provedeny následující `Then` příkazy. `True`</span><span class="sxs-lookup"><span data-stu-id="a1b84-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="a1b84-130">Pokud `condition` je `False`, každý`ElseIf` příkaz (pokud existuje) je vyhodnocen v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a1b84-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="a1b84-131">Když se najde, vyspouštějí se příkazy ihned po přidružení `ElseIf`. `True` `elseifcondition`</span><span class="sxs-lookup"><span data-stu-id="a1b84-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="a1b84-132">Pokud není `True` `ElseIf` vyhodnocena jako, nebo pokud nejsou žádné příkazy, jsou provedeny následující `Else` příkazy. `elseifcondition`</span><span class="sxs-lookup"><span data-stu-id="a1b84-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="a1b84-133">`Then`Po provedení příkazů níže `ElseIf`,, nebo `Else`, se provedení pokračuje příkazem následující `End If`.</span><span class="sxs-lookup"><span data-stu-id="a1b84-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="a1b84-134">Klauzule `ElseIf` a`Else` jsou obě volitelné.</span><span class="sxs-lookup"><span data-stu-id="a1b84-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="a1b84-135">Můžete mít tolik klauzulí, `ElseIf` kolik chcete `If`v... `Then`... , ale `ElseIf` žádná`Else` klauzule nemůže být uvedena za klauzulí. `Else`</span><span class="sxs-lookup"><span data-stu-id="a1b84-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="a1b84-136">`If`... `Then`... `Else` příkazy mohou být vnořeny do sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="a1b84-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="a1b84-137">V syntaxi `If` na více řádků musí být příkaz jediným příkazem na prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="a1b84-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="a1b84-138">Příkazům `Else` ,a`End If` lze předcházet pouze pomocí popisku čáry. `ElseIf`</span><span class="sxs-lookup"><span data-stu-id="a1b84-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="a1b84-139">`If`... `Then`... blok musí končit `End If`příkazem. `Else`</span><span class="sxs-lookup"><span data-stu-id="a1b84-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="a1b84-140">[Vybrat... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnocujete jeden výraz, který má několik možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="a1b84-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="a1b84-141">Jednoduchá čára syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-141">Single-Line syntax</span></span>

<span data-ttu-id="a1b84-142">Pomocí syntaxe na jednom řádku můžete pro jednu podmínku spustit kód, pokud je hodnota true.</span><span class="sxs-lookup"><span data-stu-id="a1b84-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="a1b84-143">Syntaxe s více řádky však poskytuje více struktury a flexibilitu a je snazší je číst, udržovat a ladit.</span><span class="sxs-lookup"><span data-stu-id="a1b84-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="a1b84-144">Co následuje `Then` klíčové slovo, je přezkoumáno pro zjištění, zda je příkaz tvořen jedním `If`řádkem.</span><span class="sxs-lookup"><span data-stu-id="a1b84-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="a1b84-145">Pokud se `Then` na stejném řádku objeví cokoli jiného než komentář, je příkaz považován za jednořádkový `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a1b84-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="a1b84-146">Pokud `Then` chybí, musí se jednat o začátek víceřádkového `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="a1b84-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="a1b84-147">V syntaxi na jednom řádku můžete mít jako výsledek výrazu `If`... více spuštěných příkazů... `Then` rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="a1b84-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="a1b84-148">Všechny příkazy musí být na stejném řádku a musí být oddělené dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="a1b84-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="a1b84-149">Příklad víceřádkové syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="a1b84-150">Následující příklad ukazuje použití víceřádkové syntaxe `If`... `Then`... `Else` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a1b84-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="a1b84-151">Příklad vnořené syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b84-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="a1b84-152">Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1b84-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="a1b84-153">Příklad syntaxe s jedním řádkem</span><span class="sxs-lookup"><span data-stu-id="a1b84-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="a1b84-154">Následující příklad ilustruje použití syntaxe na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="a1b84-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="a1b84-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1b84-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="a1b84-156">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="a1b84-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="a1b84-157">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="a1b84-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="a1b84-158">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="a1b84-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="a1b84-159">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="a1b84-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="a1b84-160">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1b84-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="a1b84-161">Operátor If</span><span class="sxs-lookup"><span data-stu-id="a1b84-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
