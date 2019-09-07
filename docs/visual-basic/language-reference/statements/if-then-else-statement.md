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
ms.openlocfilehash: db81a1c41809b563d5f9d0777c3feb064c5e540b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400714"
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

Tento článek obsahuje několik příkladů, které ilustrují použití `If`... `Then`... `Else` příkaz:

- [Příklad víceřádkové syntaxe](#multi-line)
- [Příklad vnořené syntaxe](#nested)
- [Příklad syntaxe s jedním řádkem](#single-line)

## <a name="parts"></a>Součásti

`condition` \
Povinný parametr. Vyjádření. Je nutné vyhodnotit na `True` nebo `False`, nebo na datový typ, který je implicitně převoditelný na `Boolean`.

Pokud je výraz proměnnou s [možnou hodnotou null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , která se vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), je `False`zpracována podmínka, jako by byl výraz, a `ElseIf` bloky jsou vyhodnoceny `Else` , pokud existují, nebo blok je provedeno, pokud existuje.

`Then` \
Vyžadované v syntaxi na jednom řádku; volitelné v syntaxi na více řádků.

`statements` \
Volitelný parametr. Jeden nebo více příkazů, `If`které následují... , které se spustí `condition` , pokud je `True`vyhodnoceno jako. `Then`

`elseifcondition` \
Požadováno, `ElseIf` Pokud je k dispozici. Vyjádření. Je nutné vyhodnotit na `True` nebo `False`, nebo na datový typ, který je implicitně převoditelný na `Boolean`.

`elseifstatements` \
Volitelný parametr. Jeden nebo více příkazů, `ElseIf`které následují... , které se spustí `elseifcondition` , pokud je `True`vyhodnoceno jako. `Then`

`elsestatements` \
Volitelný parametr. Jeden nebo více příkazů, které jsou spuštěny, `condition` Pokud `elseifcondition` žádný předchozí nebo výraz `True`není vyhodnocen jako.

`End If` \
Ukončí víceřádkovou verzi `If`... `Then`... `Else` blok.

## <a name="remarks"></a>Poznámky

### <a name="multiline-syntax"></a>Víceřádková syntaxe

`If`Když... `Then`... byl zjištěn příkaz, `condition` je testován. `Else` V případě `condition`,jsou provedeny následující `Then` příkazy. `True` Pokud `condition` je `False`, každý`ElseIf` příkaz (pokud existuje) je vyhodnocen v pořadí. Když se najde, vyspouštějí se příkazy ihned po přidružení `ElseIf`. `True` `elseifcondition` Pokud není `True` `ElseIf` vyhodnocena jako, nebo pokud nejsou žádné příkazy, jsou provedeny následující `Else` příkazy. `elseifcondition` `Then`Po provedení příkazů níže `ElseIf`,, nebo `Else`, se provedení pokračuje příkazem následující `End If`.

Klauzule `ElseIf` a`Else` jsou obě volitelné. Můžete mít tolik klauzulí, `ElseIf` kolik chcete `If`v... `Then`... , ale `ElseIf` žádná`Else` klauzule nemůže být uvedena za klauzulí. `Else` `If`... `Then`... `Else` příkazy mohou být vnořeny do sebe navzájem.

V syntaxi `If` na více řádků musí být příkaz jediným příkazem na prvním řádku. Příkazům `Else` ,a`End If` lze předcházet pouze pomocí popisku čáry. `ElseIf` `If`... `Then`... blok musí končit `End If`příkazem. `Else`

> [!TIP]
> [Vybrat... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnocujete jeden výraz, který má několik možných hodnot.

### <a name="single-line-syntax"></a>Jednoduchá čára syntaxe

Pomocí syntaxe na jednom řádku můžete pro jednu podmínku spustit kód, pokud je hodnota true. Syntaxe s více řádky však poskytuje více struktury a flexibilitu a je snazší je číst, udržovat a ladit.

Co následuje `Then` klíčové slovo, je přezkoumáno pro zjištění, zda je příkaz tvořen jedním `If`řádkem. Pokud se `Then` na stejném řádku objeví cokoli jiného než komentář, je příkaz považován za jednořádkový `If` příkaz. Pokud `Then` chybí, musí se jednat o začátek víceřádkového `If`... `Then`... `Else`.

V syntaxi na jednom řádku můžete mít jako výsledek výrazu `If`... více spuštěných příkazů... `Then` rozhodnutí. Všechny příkazy musí být na stejném řádku a musí být oddělené dvojtečkami.

## <a name="multiline-syntax-example"></a>Příklad víceřádkové syntaxe

<a name="multi-line"></a>

Následující příklad ukazuje použití víceřádkové syntaxe `If`... `Then`... `Else` příkaz.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Příklad vnořené syntaxe

<a name="nested"></a>

Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.

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
