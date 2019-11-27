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
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351166"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else – příkaz (Visual Basic)

Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.

## <a name="syntax"></a>Syntaxe

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

## <a name="quick-links-to-example-code"></a>Rychlé odkazy na příklad kódu

Tento článek obsahuje několik příkladů, které ilustrují použití `If`...`Then`...`Else` příkazu:

- [Příklad víceřádkové syntaxe](#multi-line)
- [Příklad vnořené syntaxe](#nested)
- [Příklad syntaxe s jedním řádkem](#single-line)

## <a name="parts"></a>Součásti

`condition` \
Požadováno. Vyjádření. Musí se vyhodnotit jako `True` nebo `False`nebo na datový typ, který je implicitně převoditelné na `Boolean`.

Pokud je výraz `Boolean` proměnnou s [možnou hodnotou null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) , která je vyhodnocena jako [Nothing](../../../visual-basic/language-reference/nothing.md), je podmínka považována za, pokud je výraz `False`a `ElseIf` bloky jsou vyhodnoceny, pokud existují, nebo je spuštěn blok `Else`, pokud existuje.

`Then` \
Vyžadované v syntaxi na jednom řádku; volitelné v syntaxi na více řádků.

`statements` \
Volitelná. Jeden nebo více příkazů, které následují `If`...`Then`, které se spustí, pokud se `condition` vyhodnotí jako `True`.

`elseifcondition` \
Vyžaduje se, pokud je `ElseIf` k dispozici. Vyjádření. Musí se vyhodnotit jako `True` nebo `False`nebo na datový typ, který je implicitně převoditelné na `Boolean`.

`elseifstatements` \
Volitelná. Jeden nebo více příkazů, které následují `ElseIf`...`Then`, které se spustí, pokud se `elseifcondition` vyhodnotí jako `True`.

`elsestatements` \
Volitelná. Jeden nebo více příkazů, které jsou provedeny, pokud žádný předchozí `condition` nebo `elseifcondition` výraz není vyhodnocen jako `True`.

`End If` \
Ukončí víceřádkovou verzi `If`...`Then`...`Else` blok.

## <a name="remarks"></a>Poznámky

### <a name="multiline-syntax"></a>Víceřádková syntaxe

Při výskytu příkazu `If`...`Then`...`Else` se testuje `condition`. Pokud je `True``condition`, jsou provedeny následující příkazy `Then`. Pokud je `condition` `False`, každý příkaz `ElseIf` (pokud existuje) se vyhodnotí v pořadí. Když se najde `elseifcondition` `True`, provedou se příkazy ihned po přidružené `ElseIf`. Pokud se žádné `elseifcondition` nevyhodnotí jako `True`nebo pokud nejsou k dispozici žádné příkazy `ElseIf`, jsou provedeny následující příkazy `Else`. Po provedení příkazů, které následují `Then`, `ElseIf`nebo `Else`, se provádění pokračuje pomocí příkazu, který následuje po `End If`.

Klauzule `ElseIf` a `Else` jsou volitelné. Můžete mít tolik klauzulí `ElseIf`, kolik chcete v příkazu `If`...`Then`...`Else`, ale žádná `ElseIf` klauzule se nemůže vyskytovat za klauzulí `Else`. `If`...`Then`...`Else` příkazy mohou být vnořeny do sebe navzájem.

V syntaxi na více řádků musí být příkaz `If` jediným příkazem na prvním řádku. Příkazům `ElseIf`, `Else`a `End If` lze předcházet pouze pomocí popisku čáry. Blok `If`...`Then`...`Else` musí končit příkazem `End If`.

> [!TIP]
> [Vybrat... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnocujete jeden výraz, který má několik možných hodnot.

### <a name="single-line-syntax"></a>Jednoduchá čára syntaxe

Pomocí syntaxe na jednom řádku můžete pro jednu podmínku spustit kód, pokud je hodnota true. Syntaxe s více řádky však poskytuje více struktury a flexibilitu a je snazší je číst, udržovat a ladit.

Následující klíčové slovo `Then` je přezkoumáno k určení, zda je příkaz jednořádkový `If`. Pokud se po `Then` na stejném řádku zobrazí něco jiného než komentář, příkaz se zpracuje jako jednořádkový `If` příkaz. Pokud `Then` chybí, musí se jednat o začátek víceřádkového `If`...`Then`...`Else`.

V syntaxi na jednom řádku můžete mít v důsledku `If`...`Then` provedení více příkazů. Všechny příkazy musí být na stejném řádku a musí být oddělené dvojtečkami.

## <a name="multiline-syntax-example"></a>Příklad víceřádkové syntaxe

<a name="multi-line"></a>

Následující příklad ilustruje použití víceřádkové syntaxe příkazu `If`...`Then`...`Else`.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Příklad vnořené syntaxe

<a name="nested"></a>

Následující příklad obsahuje vnořené příkazy `If`...`Then`...`Else`.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Příklad syntaxe s jedním řádkem

<a name="single-line"></a>Následující příklad ilustruje použití syntaxe na jednom řádku.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Rozhodovací struktury](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)
