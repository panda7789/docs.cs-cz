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
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249484"
---
# <a name="if-operator-visual-basic"></a>If – operátor (Visual Basic)

Používá vyhodnocení zkratu podmíněně vrátit jednu ze dvou hodnot. Operátor `If` lze volat se třemi argumenty nebo se dvěma argumenty.

## <a name="syntax"></a>Syntaxe

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Pokud operátor volal se třemi argumenty

Při `If` volání pomocí tří argumentů, první argument musí vyhodnotit na `Boolean`hodnotu, která může být přetypována jako . Tato `Boolean` hodnota určí, který z dalších dvou argumentů je vyhodnocen a vrácen. Následující seznam platí pouze `If` v případě, že operátor je volána pomocí tří argumentů.

### <a name="parts"></a>Součásti

|Označení|Definice|
|---|---|
|`argument1`|Povinná hodnota. `Boolean`. Určuje, které z ostatních argumentů vyhodnotit a vrátit.|
|`argument2`|Povinná hodnota. `Object`. Vyhodnotit a `argument1` vrátit, `True`pokud vyhodnotí na .|
|`argument3`|Povinná hodnota. `Object`. Vyhodnotit a `argument1` vrátit, `False` pokud `argument1` vyhodnotí nebo pokud je [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnná, která vyhodnotí [Nothing](../../../visual-basic/language-reference/nothing.md).|

Operátor, `If` který je volán se `IIf` třemi argumenty funguje jako funkce s tím rozdílem, že používá vyhodnocení zkratu. Funkce `IIf` vždy vyhodnotí všechny tři své argumenty, zatímco `If` operátor, který má tři argumenty vyhodnotí pouze dva z nich. První `If` argument je vyhodnocen a `Boolean` výsledek `True` je `False`přetypován jako hodnota nebo . Pokud je `True`hodnota `argument2` , je vyhodnocena `argument3` a její hodnota je vrácena, ale není vyhodnocena. Pokud `Boolean` je `False`hodnota výrazu `argument3` , je vyhodnocena `argument2` a jeho hodnota je vrácena, ale není vyhodnocena. Následující příklady ilustrují použití při `If` použití tří argumentů:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Následující příklad ilustruje hodnotu hodnocení zkratu. Příklad ukazuje dva pokusy `number` o `divisor` rozdělení `divisor` proměnné proměnnou s výjimkou případů, kdy je nula. V takovém případě by měla být vrácena 0 a žádný pokus by měla být provedena k provedení dělení, protože by došlo k chybě za běhu. Vzhledem `If` k tomu, že výraz používá vyhodnocení zkratu, vyhodnotí druhý nebo třetí argument v závislosti na hodnotě prvního argumentu. Pokud je splněn první argument, dělitel není nula a je bezpečné vyhodnotit druhý argument a provést dělení. Pokud je první argument false, je vyhodnocen pouze třetí argument a je vrácena 0. Proto při dělitel je 0, žádný pokus o provedení dělení a žádné výsledky chyby. Však `IIf` protože nepoužívá vyhodnocení zkratu, druhý argument je vyhodnocena i v případě, že první argument je false. To způsobí chybu dělení časem.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Pokud operátor volal se dvěma argumenty

První argument `If` lze vynechat. To umožňuje operátoru volat pomocí pouze dva argumenty. Následující seznam platí pouze `If` v případě, že operátor je volána se dvěma argumenty.

### <a name="parts"></a>Součásti

|Označení|Definice|
|---|---|
|`argument2`|Povinná hodnota. `Object`. Musí se jednat o odkaz nebo hodnotu s možnou hodnotou, jejíž hodnotu lze hodnotit. Vyhodnocena a vrácena, `Nothing`když se vyhodnotí na něco jiného než .|
|`argument3`|Povinná hodnota. `Object`. Vyhodnotit a `argument2` vrátit, `Nothing`pokud vyhodnotí na .|

Pokud `Boolean` je argument vynechán, první argument musí být odkaz nebo typ hodnoty s hodnotou, kterou lze hodnotit. Pokud první argument vyhodnotí `Nothing`, je vrácena hodnota druhého argumentu. Ve všech ostatních případech je vrácena hodnota první argument. Následující příklad ukazuje, jak toto hodnocení funguje:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy hodnot s povolenou hodnotou Null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nic](../nothing.md)
