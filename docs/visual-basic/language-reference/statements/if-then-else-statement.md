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

Tento článek obsahuje několik příkladů, které ilustrují použití `If` ... `Then` ...`Else` vydá

- [Příklad víceřádkové syntaxe](#multi-line)
- [Příklad vnořené syntaxe](#nested)
- [Příklad syntaxe s jedním řádkem](#single-line)

## <a name="parts"></a>Součásti

`condition` \
Povinná hodnota. Vyjádření. Je nutné vyhodnotit na `True` nebo `False` , nebo na datový typ, který je implicitně převoditelný na `Boolean` .

Pokud je výraz proměnnou s [možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , která se vyhodnotí jako [Nothing](../nothing.md), je zpracována podmínka, jako by byl výraz `False` , a `ElseIf` bloky jsou vyhodnoceny, pokud existují, nebo `Else` Pokud je spuštěn blok, pokud existuje.

`Then` \
Vyžadované v syntaxi na jednom řádku; volitelné v syntaxi na více řádků.

`statements` \
Nepovinný parametr. Jeden nebo více příkazů `If` , které následují... `Then` , které se spustí, pokud je `condition` vyhodnocena jako `True` .

`elseifcondition` \
Požadováno `ElseIf` , pokud je k dispozici. Vyjádření. Je nutné vyhodnotit na `True` nebo `False` , nebo na datový typ, který je implicitně převoditelný na `Boolean` .

`elseifstatements` \
Nepovinný parametr. Jeden nebo více příkazů `ElseIf` , které následují... `Then` , které se spustí, pokud je `elseifcondition` vyhodnocena jako `True` .

`elsestatements` \
Nepovinný parametr. Jeden nebo více příkazů, které jsou spuštěny, pokud žádný předchozí `condition` nebo `elseifcondition` výraz není vyhodnocen jako `True` .

`End If` \
Ukončí víceřádkovou verzi `If` ... `Then` ...`Else` Blokované.

## <a name="remarks"></a>Poznámky

### <a name="multiline-syntax"></a>Víceřádková syntaxe

Když `If` ... `Then` ...`Else` byl zjištěn příkaz, `condition` je testován. `condition`V případě `True` , `Then` jsou provedeny následující příkazy. Pokud `condition` je `False` , každý `ElseIf` příkaz (pokud existuje) je vyhodnocen v pořadí. Když `True` `elseifcondition` se najde, vyspouštějí se příkazy ihned po přidružení `ElseIf` . Pokud není `elseifcondition` vyhodnocena jako `True` , nebo pokud nejsou žádné `ElseIf` příkazy, `Else` jsou provedeny následující příkazy. Po provedení příkazů níže, `Then` `ElseIf` , nebo, se `Else` provedení pokračuje příkazem následující `End If` .

`ElseIf`Klauzule a `Else` jsou obě volitelné. Můžete mít tolik klauzulí, kolik `ElseIf` chcete v `If` ... `Then` ...`Else` , ale žádná `ElseIf` klauzule nemůže být uvedena za `Else` klauzulí. `If`...`Then` ...`Else` příkazy mohou být vnořeny do sebe navzájem.

V syntaxi na více řádků `If` musí být příkaz jediným příkazem na prvním řádku. `ElseIf` `Else` Příkazům, a `End If` lze předcházet pouze pomocí popisku čáry. . `If` .. `Then` ...`Else` blok musí končit `End If` příkazem.

> [!TIP]
> [Vybrat... Příkaz Case](select-case-statement.md) může být užitečnější, pokud vyhodnocujete jeden výraz, který má několik možných hodnot.

### <a name="single-line-syntax"></a>Jednoduchá čára syntaxe

Pomocí syntaxe na jednom řádku můžete pro jednu podmínku spustit kód, pokud je hodnota true. Syntaxe s více řádky však poskytuje více struktury a flexibilitu a je snazší je číst, udržovat a ladit.

Co následuje `Then` klíčové slovo, je přezkoumáno pro zjištění, zda je příkaz tvořen jedním řádkem `If` . Pokud se na stejném řádku objeví cokoli jiného než komentář `Then` , je příkaz považován za jednořádkový `If` příkaz. Pokud `Then` chybí, musí se jednat o začátek víceřádkového `If` ... `Then` ...`Else`.

V syntaxi na jednom řádku můžete mít v důsledku `If` rozhodnutí typu... vykonané více příkazů. `Then` Všechny příkazy musí být na stejném řádku a musí být oddělené dvojtečkami.

## <a name="multiline-syntax-example"></a>Příklad víceřádkové syntaxe

<a name="multi-line"></a>

Následující příklad ukazuje použití víceřádkové syntaxe `If` ... `Then` ...`Else` vydá.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Příklad vnořené syntaxe

<a name="nested"></a>

Následující příklad obsahuje vnořené `If` ... `Then` ...`Else` učiněn.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Příklad syntaxe s jedním řádkem

<a name="single-line"></a>Následující příklad ilustruje použití syntaxe na jednom řádku.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If... Then... #Else – direktivy](../directives/if-then-else-directives.md)
- [Select...Case – příkaz](select-case-statement.md)
- [Vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Struktury rozhodování](../../programming-guide/language-features/control-flow/decision-structures.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If – operátor](../operators/if-operator.md)
