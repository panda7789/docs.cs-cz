---
title: Typy hodnot s povolenou hodnotou Null
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
ms.openlocfilehash: 0d259e11a969f4eb7e64626a4adf498db06ece06
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347842"
---
# <a name="nullable-value-types-visual-basic"></a>Typy hodnot s povolenou hodnotou Null (Visual Basic)

Někdy pracujete s typem hodnoty, který nemá v určitých případech definovanou hodnotu. Například pole v databázi může být nutné rozlišovat mezi přiřazením přiřazené hodnoty, která je smysluplná a nemá přiřazenou hodnotu. Typy hodnot lze rozšířit tak, aby převzaly jejich normální hodnoty nebo hodnotu null. Takové rozšíření se nazývá typ s *možnou hodnotou null*.

Každý typ s možnou hodnotou null je vytvořen z obecné struktury <xref:System.Nullable%601>. Vezměte v úvahu databázi, která sleduje aktivity související s prací. Následující příklad vytvoří `Boolean` typ s možnou hodnotou null a deklaruje proměnnou daného typu. Deklaraci můžete zapsat třemi způsoby:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Proměnná `ridesBusToWork` může obsahovat hodnotu `True`, hodnotu `False`nebo žádnou hodnotu. Počáteční výchozí hodnota není vůbec žádná hodnota, což by v tomto případě mohlo znamenat, že pro tuto osobu ještě nebyly získány informace. Na rozdíl od `False` může znamenat, že byly informace získány a osoba nepracovala sběrnici k fungování.

Můžete deklarovat proměnné a vlastnosti s typy s možnou hodnotou null a můžete deklarovat pole s prvky typu s možnou hodnotou null. Můžete deklarovat procedury s typy s možnou hodnotou null jako parametry a můžete z `Function` procedury vrátit typ s možnou hodnotou null.

Typ s možnou hodnotou null nelze vytvořit v typu odkazu, jako je pole, `String`nebo třída. Nadřízený typ musí být hodnotový typ. Další informace naleznete v tématu [typy hodnot a typy odkazů](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Použití proměnné typu s možnou hodnotou null

Nejdůležitějšími členy typu s možnou hodnotou null jsou jeho <xref:System.Nullable%601.HasValue%2A> a vlastnosti <xref:System.Nullable%601.Value%2A>. Pro proměnnou typu s možnou hodnotou null <xref:System.Nullable%601.HasValue%2A> oznamuje, zda proměnná obsahuje definovanou hodnotu. Pokud je <xref:System.Nullable%601.HasValue%2A> `True`, můžete si přečíst hodnotu z <xref:System.Nullable%601.Value%2A>. Všimněte si, že <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> jsou `ReadOnly` vlastnosti.

### <a name="default-values"></a>Výchozí hodnoty

Pokud deklarujete proměnnou s typem s možnou hodnotou null, má vlastnost <xref:System.Nullable%601.HasValue%2A> výchozí hodnotu `False`. To znamená, že ve výchozím nastavení proměnná nemá žádnou definovanou hodnotu namísto výchozí hodnoty svého základního typu hodnoty. V následujícím příkladu proměnná `numberOfChildren` zpočátku nemá definovanou hodnotu, i když je výchozí hodnota `Integer` typu 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Hodnota null je užitečná k označení nedefinované nebo neznámé hodnoty. Pokud byla `numberOfChildren` deklarována jako `Integer`, neexistuje žádná hodnota, která by mohla znamenat, že informace nejsou aktuálně k dispozici.

### <a name="storing-values"></a>Ukládání hodnot

Hodnotu můžete v proměnné nebo vlastnosti typu s možnou hodnotou null ukládat obvyklým způsobem. Následující příklad přiřadí hodnotu proměnné `numberOfChildren` deklarované v předchozím příkladu.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Pokud proměnná nebo vlastnost typu s možnou hodnotou null obsahuje definovanou hodnotu, můžete to způsobit, že se vrátí do svého počátečního stavu, který nemá přiřazenou hodnotu. To provedete tak, že nastavíte proměnnou nebo vlastnost na `Nothing`, jak ukazuje následující příklad.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> I když můžete přiřadit `Nothing` k proměnné typu s možnou hodnotou null, nemůžete ji otestovat pro `Nothing` pomocí znaménka rovná se. Porovnání, které používá rovnítko, `someVar = Nothing`, se vždy vyhodnocuje jako `Nothing`. Můžete otestovat vlastnost <xref:System.Nullable%601.HasValue%2A> proměnné pro `False`nebo otestovat pomocí operátoru `Is` nebo `IsNot`.

### <a name="retrieving-values"></a>Načítání hodnot

Chcete-li načíst hodnotu proměnné typu s možnou hodnotou null, měli byste nejprve otestovat jeho vlastnost <xref:System.Nullable%601.HasValue%2A> a potvrdit, že má hodnotu. Pokud se pokusíte přečíst hodnotu, když je <xref:System.Nullable%601.HasValue%2A> `False`, Visual Basic vyvolá výjimku <xref:System.InvalidOperationException>. Následující příklad ukazuje doporučený způsob, jak číst proměnnou `numberOfChildren` předchozích příkladech.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Porovnání typů s možnou hodnotou null

Pokud jsou v logických výrazech použity `Boolean` proměnné s hodnotou null, může být výsledek `True`, `False`nebo `Nothing`. Následuje tabulka pravdy pro `And` a `Or`. Vzhledem k tomu, že `b1` a `b2` nyní mají tři možné hodnoty, existují devět kombinací pro vyhodnocení.

|b1|b2|B1 a B2|B1 nebo B2|
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

Pokud je hodnota logické proměnné nebo výrazu `Nothing`, není `true` ani `false`. Zamyslete se nad následujícím příkladem.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

V tomto příkladu se `b1 And b2` vyhodnocuje jako `Nothing`. V důsledku toho je klauzule `Else` spuštěna v každém příkazu `If` a výstup je následující:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` a `OrElse`, které používají testování po krátkém okruhu, musí při prvním vyhodnocení na `Nothing`vyhodnotit jejich druhý operand.

## <a name="propagation"></a>Šíření

V případě, že jeden nebo oba operandy aritmetické operace, porovnání, posunu nebo typu může mít hodnotu null, výsledek operace je také možnou hodnotou null. Pokud mají oba operandy hodnoty, které nejsou `Nothing`, operace se provádí na podkladových hodnotách operandů, jako by nebyl typ s možnou hodnotou null. V následujícím příkladu jsou proměnné `compare1` a `sum1` implicitně typové. Pokud ponecháte ukazatel myši nad nimi, uvidíte, že kompilátor odvodí u obou z nich typy s možnou hodnotou null.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Pokud jeden nebo oba operandy mají hodnotu `Nothing`, výsledek bude `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Použití typů s povolenou hodnotou null s daty

Databáze je jedním z nejdůležitějších míst pro použití typů s možnou hodnotou null. Ne všechny objekty databáze aktuálně podporují typy s možnou hodnotou null, ale adaptéry tabulek vygenerované návrhářem. Viz [Podpora TableAdapter pro typy s možnou hodnotou null](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Viz také:

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Datové typy](index.md)
- [Typy hodnot a odkazové typy](value-types-and-reference-types.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Vyplnění datových sad pomocí objektů TableAdapter](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [Operátor If](../../../language-reference/operators/if-operator.md)
- [Odvození místního typu](../variables/local-type-inference.md)
- [Operátor Is](../../../language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../language-reference/operators/isnot-operator.md)
- [Typy hodnot s možnou hodnotou null (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
