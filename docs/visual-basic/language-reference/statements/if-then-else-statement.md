---
title: If...Then...Else – příkaz
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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404586"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="5bb2b-102">If...Then...Else – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bb2b-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="5bb2b-103">Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="5bb2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-104">Syntax</span></span>

```vb
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="5bb2b-105">Rychlé odkazy na příklad kódu</span><span class="sxs-lookup"><span data-stu-id="5bb2b-105">Quick links to example code</span></span>

<span data-ttu-id="5bb2b-106">Tento článek obsahuje několik příkladů, které ilustrují použití `If` ... `Then` ...`Else` vydá</span><span class="sxs-lookup"><span data-stu-id="5bb2b-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="5bb2b-107">Příklad víceřádkové syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="5bb2b-108">Příklad vnořené syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="5bb2b-109">Příklad syntaxe s jedním řádkem</span><span class="sxs-lookup"><span data-stu-id="5bb2b-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="5bb2b-110">Součásti</span><span class="sxs-lookup"><span data-stu-id="5bb2b-110">Parts</span></span>

`condition` \
<span data-ttu-id="5bb2b-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-111">Required.</span></span> <span data-ttu-id="5bb2b-112">Vyjádření.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-112">Expression.</span></span> <span data-ttu-id="5bb2b-113">Je nutné vyhodnotit na `True` nebo `False` , nebo na datový typ, který je implicitně převoditelný na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="5bb2b-114">Pokud je výraz proměnnou s [možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , která se vyhodnotí jako [Nothing](../nothing.md), je zpracována podmínka, jako by byl výraz `False` , a `ElseIf` bloky jsou vyhodnoceny, pokud existují, nebo `Else` Pokud je spuštěn blok, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-114">If the expression is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="5bb2b-115">Vyžadované v syntaxi na jednom řádku; volitelné v syntaxi na více řádků.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="5bb2b-116">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-116">Optional.</span></span> <span data-ttu-id="5bb2b-117">Jeden nebo více příkazů `If` , které následují... `Then` , které se spustí, pokud je `condition` vyhodnocena jako `True` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="5bb2b-118">Požadováno `ElseIf` , pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="5bb2b-119">Vyjádření.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-119">Expression.</span></span> <span data-ttu-id="5bb2b-120">Je nutné vyhodnotit na `True` nebo `False` , nebo na datový typ, který je implicitně převoditelný na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="5bb2b-121">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-121">Optional.</span></span> <span data-ttu-id="5bb2b-122">Jeden nebo více příkazů `ElseIf` , které následují... `Then` , které se spustí, pokud je `elseifcondition` vyhodnocena jako `True` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="5bb2b-123">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-123">Optional.</span></span> <span data-ttu-id="5bb2b-124">Jeden nebo více příkazů, které jsou spuštěny, pokud žádný předchozí `condition` nebo `elseifcondition` výraz není vyhodnocen jako `True` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="5bb2b-125">Ukončí víceřádkovou verzi `If` ... `Then` ...`Else` Blokované.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bb2b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bb2b-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="5bb2b-127">Víceřádková syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-127">Multiline syntax</span></span>

<span data-ttu-id="5bb2b-128">Když `If` ... `Then` ...`Else` byl zjištěn příkaz, `condition` je testován.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="5bb2b-129">`condition`V případě `True` , `Then` jsou provedeny následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="5bb2b-130">Pokud `condition` je `False` , každý `ElseIf` příkaz (pokud existuje) je vyhodnocen v pořadí.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="5bb2b-131">Když `True` `elseifcondition` se najde, vyspouštějí se příkazy ihned po přidružení `ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="5bb2b-132">Pokud není `elseifcondition` vyhodnocena jako `True` , nebo pokud nejsou žádné `ElseIf` příkazy, `Else` jsou provedeny následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="5bb2b-133">Po provedení příkazů níže, `Then` `ElseIf` , nebo, se `Else` provedení pokračuje příkazem následující `End If` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="5bb2b-134">`ElseIf`Klauzule a `Else` jsou obě volitelné.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="5bb2b-135">Můžete mít tolik klauzulí, kolik `ElseIf` chcete v `If` ... `Then` ...`Else` , ale žádná `ElseIf` klauzule nemůže být uvedena za `Else` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="5bb2b-136">`If`...`Then` ...`Else` příkazy mohou být vnořeny do sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="5bb2b-137">V syntaxi na více řádků `If` musí být příkaz jediným příkazem na prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="5bb2b-138">`ElseIf` `Else` Příkazům, a `End If` lze předcházet pouze pomocí popisku čáry.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="5bb2b-139">. `If` .. `Then` ...`Else` blok musí končit `End If` příkazem.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="5bb2b-140">[Vybrat... Příkaz Case](select-case-statement.md) může být užitečnější, pokud vyhodnocujete jeden výraz, který má několik možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-140">The [Select...Case Statement](select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="5bb2b-141">Jednoduchá čára syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-141">Single-Line syntax</span></span>

<span data-ttu-id="5bb2b-142">Pomocí syntaxe na jednom řádku můžete pro jednu podmínku spustit kód, pokud je hodnota true.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="5bb2b-143">Syntaxe s více řádky však poskytuje více struktury a flexibilitu a je snazší je číst, udržovat a ladit.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="5bb2b-144">Co následuje `Then` klíčové slovo, je přezkoumáno pro zjištění, zda je příkaz tvořen jedním řádkem `If` .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="5bb2b-145">Pokud se na stejném řádku objeví cokoli jiného než komentář `Then` , je příkaz považován za jednořádkový `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="5bb2b-146">Pokud `Then` chybí, musí se jednat o začátek víceřádkového `If` ... `Then` ...`Else`.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="5bb2b-147">V syntaxi na jednom řádku můžete mít v důsledku `If` rozhodnutí typu... vykonané více příkazů. `Then`</span><span class="sxs-lookup"><span data-stu-id="5bb2b-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="5bb2b-148">Všechny příkazy musí být na stejném řádku a musí být oddělené dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="5bb2b-149">Příklad víceřádkové syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="5bb2b-150">Následující příklad ukazuje použití víceřádkové syntaxe `If` ... `Then` ...`Else` vydá.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="5bb2b-151">Příklad vnořené syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bb2b-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="5bb2b-152">Následující příklad obsahuje vnořené `If` ... `Then` ...`Else` učiněn.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="5bb2b-153">Příklad syntaxe s jedním řádkem</span><span class="sxs-lookup"><span data-stu-id="5bb2b-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="5bb2b-154">Následující příklad ilustruje použití syntaxe na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="5bb2b-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bb2b-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="5bb2b-156">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="5bb2b-156">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
- [<span data-ttu-id="5bb2b-157">Select...Case – příkaz</span><span class="sxs-lookup"><span data-stu-id="5bb2b-157">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="5bb2b-158">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="5bb2b-158">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5bb2b-159">Struktury rozhodování</span><span class="sxs-lookup"><span data-stu-id="5bb2b-159">Decision Structures</span></span>](../../programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="5bb2b-160">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bb2b-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="5bb2b-161">If – operátor</span><span class="sxs-lookup"><span data-stu-id="5bb2b-161">If Operator</span></span>](../operators/if-operator.md)
