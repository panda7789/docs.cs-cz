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
ms.openlocfilehash: 28fb2afb2c4cf78ffbbb028145de647a8dc512ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371100"
---
# <a name="if-operator-visual-basic"></a>If – operátor (Visual Basic)

Nástroj používá k podmíněnému vrácení jedné ze dvou hodnot hodnocení krátkodobého okruhu. `If`Operátor lze volat se třemi argumenty nebo dvěma argumenty.

## <a name="syntax"></a>Syntaxe

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>If volal operátor se třemi argumenty

Když `If` je volána pomocí tří argumentů, první argument musí být vyhodnocen na hodnotu, která může být převedena jako `Boolean` . Tato `Boolean` hodnota určí, který z dalších dvou argumentů bude vyhodnocen a vrácen. Následující seznam platí pouze v případě, že `If` je operátor volán pomocí tří argumentů.

### <a name="parts"></a>Součásti

|Pojem|Definice|
|---|---|
|`argument1`|Povinná hodnota. `Boolean`. Určuje, který z dalších argumentů má být vyhodnocen a vrácen.|
|`argument2`|Povinná hodnota. `Object`. Vyhodnoceno a vráceno, pokud `argument1` je vyhodnoceno jako `True` .|
|`argument3`|Povinná hodnota. `Object`. Vyhodnoceno a vráceno `argument1` , pokud se vyhodnotí jako `False` Proměnná s `argument1` [možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , která je vyhodnocena jako [Nothing](../nothing.md).|

`If`Operátor, který je volán se třemi argumenty, funguje jako `IIf` funkce s tím rozdílem, že používá testování pomocí krátkodobého okruhu. `IIf`Funkce vždy vyhodnocuje všechny tři argumenty, zatímco `If` operátor, který má tři argumenty, vyhodnocuje pouze dva z nich. První `If` argument je vyhodnocen a výsledek je převeden jako `Boolean` hodnota `True` nebo `False` . Pokud je hodnota `True` , `argument2` je vyhodnocena a vrátí se její hodnota, ale není `argument3` vyhodnocena. Pokud je hodnota `Boolean` výrazu `False` `argument3` vyhodnocena a je vrácena jeho hodnota, ale není `argument2` vyhodnocena. Následující příklady ilustrují použití `If` při použití tří argumentů:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Následující příklad znázorňuje hodnotu vyhodnocování krátkodobého okruhu. Příklad ukazuje dva pokusy o rozdělení proměnné `number` podle proměnné, `divisor` s výjimkou případů `divisor` , kdy je nula. V takovém případě by měl být vrácen 0 a žádný pokus o provedení dělení, protože by došlo k chybě za běhu. Vzhledem k tomu `If` , že výraz používá vyhodnocování krátkých okruhů, vyhodnocuje buď druhý, nebo třetí argument v závislosti na hodnotě prvního argumentu. Pokud je první argument true, dělitel není nula a je bezpečné vyhodnotit druhý argument a provést dělení. Pokud je první argument false, je vyhodnocen pouze třetí argument a je vrácena hodnota 0. Proto pokud je dělitel 0, není proveden žádný pokus o provedení dělení a žádné výsledky chyby. Vzhledem k tomu, že `IIf` nepoužívá vyhodnocování krátkých okruhů, je druhý argument vyhodnocen i v případě, že je první argument nepravdivý. Tím dojde k chybě dělení nulou v době běhu.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>If volal operátor se dvěma argumenty

První argument, který `If` může být vynechán. To umožňuje operátorovi zavolat pouze pomocí dvou argumentů. Následující seznam platí pouze v případě, že `If` je operátor volán se dvěma argumenty.

### <a name="parts"></a>Součásti

|Pojem|Definice|
|---|---|
|`argument2`|Povinná hodnota. `Object`. Musí se jednat o odkaz nebo typ hodnoty s možnou hodnotou null. Vyhodnoceno a vráceno, když se vyhodnotí jako cokoli jiného než `Nothing` .|
|`argument3`|Povinná hodnota. `Object`. Vyhodnoceno a vráceno, pokud `argument2` je vyhodnoceno jako `Nothing` .|

Při `Boolean` vynechání argumentu musí být prvním argumentem odkaz nebo typ hodnoty s možnou hodnotou null. Pokud je první argument vyhodnocen jako `Nothing` , je vrácena hodnota druhého argumentu. Ve všech ostatních případech je vrácena hodnota prvního argumentu. Následující příklad ukazuje, jak Toto vyhodnocení funguje:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy hodnot s možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
