---
title: Typy s možnou hodnotou - jazyka Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921309"
---
# <a name="nullable-value-types-visual-basic"></a>Typy hodnot s povolenou hodnotou Null (Visual Basic)

Někdy můžete pracovat se hodnotový typ, který nemá definovanou hodnotu za určitých okolností. Například pole v databázi může mít k rozlišení mezi s přiřazenou hodnotu, která má smysl a nemají přiřazenou hodnotu. Typy hodnot je možné rozšířit na přijmout jejich normální hodnoty nebo hodnota null. Toto rozšíření je volána *typ připouštějící hodnotu Null*.

Každý typ s možnou hodnotou null je vytvořen z obecného <xref:System.Nullable%601> struktury. Vezměte v úvahu databázi, která sleduje aktivity související s prací. Následující příklad vytvoří s povolenou hodnotou Null `Boolean` zadejte a deklaruje proměnnou daného typu. Deklarace může zapisovat třemi způsoby:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Proměnná `ridesBusToWork` může obsahovat hodnotu `True`, hodnota `False`, nebo vůbec žádnou hodnotu. Počáteční výchozí hodnota je žádná hodnota, která v tomto případě může znamenat, že informace nebyl dosud byl získán tuto osobu. Naproti tomu `False` může znamenat, že byly získány informace a osoby není svézt sběrnice fungovat.

Můžete deklarovat proměnné a vlastností s typy s možnou hodnotou Null a je možné deklarovat pole s prvky typu s možnou hodnotou Null. Postupy lze deklarovat s typy s možnou hodnotou null jako parametry a může vrátit typ připouštějící hodnotu Null z `Function` postup.

Nelze vytvořit typ připouštějící hodnotu Null na typ odkazu, jako je například pole, `String`, ani o třídu. Základní typ musí být typem hodnoty. Další informace najdete v tématu [typy hodnot a odkazové typy](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Použití proměnné typu s možnou hodnotou Null

Nejdůležitější členy typu s možnou hodnotou Null jsou jeho <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> vlastnosti. Pro proměnné typu s možnou hodnotou Null <xref:System.Nullable%601.HasValue%2A> zjistíte, zda proměnná obsahuje hodnotu definovanou. Pokud <xref:System.Nullable%601.HasValue%2A> je `True`, lze odečíst hodnotu z <xref:System.Nullable%601.Value%2A>. Všimněte si, že oba <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> jsou `ReadOnly` vlastnosti.

### <a name="default-values"></a>Výchozí hodnoty

Pokud deklarujete proměnnou s typem s možnou hodnotou Null jeho <xref:System.Nullable%601.HasValue%2A> vlastnost má výchozí hodnotu `False`. To znamená, že ve výchozím nastavení proměnná nemá žádnou hodnotu definované, namísto výchozí hodnoty jeho nadřízeného typu hodnoty. V následujícím příkladu je proměnná `numberOfChildren` nemá zpočátku definovanou hodnotu, i když výchozí hodnota `Integer` typ je 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Hodnota null, je vhodné upozornit nebo nedefinovanou hodnotou. Pokud `numberOfChildren` by byl deklarován jako `Integer`, by existovat žádná hodnota, která může znamenat, že informace není aktuálně k dispozici.

### <a name="storing-values"></a>Ukládání hodnot

Uložení hodnoty v proměnné nebo vlastnosti typu s možnou hodnotou Null obvyklým způsobem. Následující příklad přiřadí hodnotu k proměnné `numberOfChildren` deklarované v předchozím příkladu.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Pokud proměnnou nebo vlastnost s možnou hodnotou Null typu obsahuje hodnotu definované, vám může způsobit, že chcete vrátit do původního stavu z nemají přiřazenu hodnotu. To provedete tak, že nastavíte proměnnou nebo vlastnost `Nothing`, jak ukazuje následující příklad.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> I když můžete přiřadit `Nothing` na proměnnou typu s možnou hodnotou Null, nelze ji pro testování `Nothing` pomocí znaménka rovnosti. Porovnání, které používá znaménka rovnosti `someVar = Nothing`, vždycky vyhodnotí jako `Nothing`. Proměnné můžete otestovat <xref:System.Nullable%601.HasValue%2A> vlastnost `False`, nebo testovat pomocí `Is` nebo `IsNot` operátor.

### <a name="retrieving-values"></a>Načítání hodnot

K načtení hodnoty proměnné typu s možnou hodnotou Null, měli byste nejprve otestovat jeho <xref:System.Nullable%601.HasValue%2A> vlastnost a ověřte, že má hodnotu. Pokud se pokusíte načíst hodnotu při <xref:System.Nullable%601.HasValue%2A> je `False`, Visual Basic vyvolá <xref:System.InvalidOperationException> výjimky. Následující příklad ukazuje doporučený způsob čtení proměnné `numberOfChildren` z předchozích příkladů.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Porovnání typů s povolenou hodnotou Null

Když s možnou hodnotou Null `Boolean` proměnné se používají v logických výrazů, výsledkem mohou být `True`, `False`, nebo `Nothing`. Následuje tabulka pravdivých informací pro `And` a `Or`. Protože `b1` a `b2` teď mají tři možné hodnoty jsou devět kombinací k vyhodnocení.

|b1|b2|B1 a b2|B1 a b2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

Pokud je hodnotou proměnné typu Boolean nebo výrazu `Nothing`, není ani `true` ani `false`. Podívejte se na následující příklad.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

V tomto příkladu `b1 And b2` vyhodnotí jako `Nothing`. V důsledku toho `Else` klauzule je proveden v každém `If` příkaz a výstup je následující:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` a `OrElse`, kteří používají krátká smyčka – vyhodnocení, se musí vyhodnotit operandy druhý při vyhodnocen jako první `Nothing`.

## <a name="propagation"></a>Šíření

Pokud je jeden nebo oba operandy aritmetického, porovnání, shift nebo typ operace s možnou hodnotou Null, je také výsledek operace s možnou hodnotou Null. Pokud mají oba operandy hodnoty, které nejsou `Nothing`, se operace provádí v podkladové hodnoty operandy, jako kdyby byly ani jeden typ připouštějící hodnotu Null. V následujícím příkladu, proměnné `compare1` a `sum1` jsou implicitně typované. Pokud je ukazatel myši nad nimi, uvidíte, že kompilátor odvodí typy připouštějící hodnotu Null u obou z nich.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Pokud máte jeden nebo oba operandy hodnotu `Nothing`, výsledkem bude `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Použití typů s povolenou hodnotou Null s daty

Databáze je jedním z nejdůležitějších místa k použití s povolenou hodnotou Null. Ne všechny databázové objekty aktuálně podporují typy připouštějící hodnotu Null, ale proveďte adaptéry tabulek generovaný návrhářem. Zobrazit [třída TableAdapter podporuje typy s možnou hodnotou Null](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Viz také:

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Použití typů s povolenou hodnotou Null](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Datové typy](index.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Vyplnění datové sady s použitím objektů TableAdapter](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If – operátor](../../../language-reference/operators/if-operator.md)
- [Odvození místního typu](../variables/local-type-inference.md)
- [Is – operátor](../../../language-reference/operators/is-operator.md)
- [IsNot – operátor](../../../language-reference/operators/isnot-operator.md)