---
title: If – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 6d25519dac31dc91f8560fd3252ba3e2622de370
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331006"
---
# <a name="if-operator-visual-basic"></a>If – operátor (Visual Basic)

Nástroj používá k podmíněnému vrácení jedné ze dvou hodnot hodnocení krátkodobého okruhu. Operátor `If` lze volat se třemi argumenty nebo dvěma argumenty.

## <a name="syntax"></a>Syntaxe

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>If volal operátor se třemi argumenty

Když je `If` volána pomocí tří argumentů, první argument musí být vyhodnocen na hodnotu, která může být převedena jako `Boolean`. Tato `Boolean` hodnota určuje, který z dalších dvou argumentů bude vyhodnocen a vrácen. Následující seznam platí pouze v případě, že je operátor `If` volán pomocí tří argumentů.

### <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`argument1`|Požadováno. `Boolean`. Určuje, který z dalších argumentů má být vyhodnocen a vrácen.|
|`argument2`|Požadováno. `Object`. Vyhodnoceno a vráceno, pokud `argument1` vyhodnocuje jako `True`.|
|`argument3`|Požadováno. `Object`. Vyhodnoceno a vráceno, pokud `argument1` vyhodnocuje jako `False` nebo pokud `argument1` je`Boolean` proměnná s [možnou hodnotou null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) , která je vyhodnocena jako [Nothing](../../../visual-basic/language-reference/nothing.md).|

Operátor `If`, který se nazývá se třemi argumenty, funguje jako `IIf` funkce s tím rozdílem, že používá testování pomocí krátkého okruhu. Funkce `IIf` vždy vyhodnocuje všechny tři argumenty, zatímco operátor `If`, který má tři argumenty, vyhodnocuje pouze dva z nich. Vyhodnotí se první argument `If` a výsledek se přetypování jako `Boolean` hodnota, `True` nebo `False`. Pokud je hodnota `True`, vyhodnotí se `argument2` a vrátí se její hodnota, ale `argument3` není vyhodnocena. Pokud je hodnota výrazu `Boolean` `False`, je vyhodnocen `argument3` a jeho hodnota je vrácena, ale `argument2` není vyhodnocena. Následující příklady ilustrují použití `If`, když se používají tři argumenty:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Následující příklad znázorňuje hodnotu vyhodnocování krátkodobého okruhu. Příklad ukazuje dva pokusy o dělení `number` proměnných podle proměnných `divisor` kromě případů, kdy je `divisor` nula. V takovém případě by měl být vrácen 0 a žádný pokus o provedení dělení, protože by došlo k chybě za běhu. Vzhledem k tomu, že výraz `If` používá testování pomocí krátkého okruhu, vyhodnocuje buď druhý, nebo třetí argument v závislosti na hodnotě prvního argumentu. Pokud je první argument true, dělitel není nula a je bezpečné vyhodnotit druhý argument a provést dělení. Pokud je první argument false, je vyhodnocen pouze třetí argument a je vrácena hodnota 0. Proto pokud je dělitel 0, není proveden žádný pokus o provedení dělení a žádné výsledky chyby. Vzhledem k tomu, že `IIf` nepoužívá vyhodnocování krátkých okruhů, je druhý argument vyhodnocen i v případě, že je první argument nepravdivý. Tím dojde k chybě dělení nulou v době běhu.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>If volal operátor se dvěma argumenty

První argument pro `If` lze vynechat. To umožňuje operátorovi zavolat pouze pomocí dvou argumentů. Následující seznam platí pouze v případě, že je operátor `If` volán se dvěma argumenty.

### <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`argument2`|Požadováno. `Object`. Musí se jednat o odkaz nebo typ s možnou hodnotou null. Vyhodnoceno a vráceno, když se vyhodnotí jako cokoli jiného než `Nothing`.|
|`argument3`|Požadováno. `Object`. Vyhodnoceno a vráceno, pokud `argument2` vyhodnocuje jako `Nothing`.|

Při vynechání argumentu `Boolean` musí být prvním argumentem odkaz nebo typ s možnou hodnotou null. Pokud je první argument vyhodnocen jako `Nothing`, je vrácena hodnota druhého argumentu. Ve všech ostatních případech je vrácena hodnota prvního argumentu. Následující příklad ukazuje, jak Toto vyhodnocení funguje:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy hodnot s povolenou hodnotou Null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
