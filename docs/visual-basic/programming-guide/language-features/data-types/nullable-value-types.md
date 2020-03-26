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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249679"
---
# <a name="nullable-value-types-visual-basic"></a>Typy hodnot s povolenou hodnotou Null (Visual Basic)

Někdy pracujete s typem hodnoty, který za určitých okolností nemá definovanou hodnotu. Například pole v databázi může mít rozlišovat mezi s přiřazenou hodnotu, která je smysluplná a nemá přiřazenou hodnotu. Typy hodnot lze rozšířit tak, aby jejich normální hodnoty nebo nulovou hodnotu. Takové rozšíření se nazývá *typ s možnou hodnotou null*.

Každý typ hodnoty s možnou <xref:System.Nullable%601> hodnotou null je vytvořen z obecné struktury. Zvažte databázi, která sleduje pracovní aktivity. Následující příklad vytvoří typ `Boolean` s možnou hodnotou null a deklaruje proměnnou tohoto typu. Prohlášení můžete napsat třemi způsoby:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Proměnná `ridesBusToWork` může obsahovat `True`hodnotu `False`, hodnotu nebo vůbec žádnou hodnotu. Jeho počáteční výchozí hodnota není vůbec žádná hodnota, což by v tomto případě mohlo znamenat, že informace ještě nebyly získány pro tuto osobu. Naproti tomu `False` by mohlo znamenat, že informace byly získány a osoba nejezdí autobusem do práce.

Můžete deklarovat proměnné a vlastnosti s typy hodnot s hodnotou s hodnotou null a můžete deklarovat pole s prvky typu hodnoty s možnou hodnotou, kterou lze hodnotit. Můžete deklarovat procedury s nulovými typy hodnot jako parametry `Function` a můžete vrátit typ hodnoty s možnou hodnotou s možnou hodnotou z procedury.

Nelze vytvořit typ s možnou hodnotou null pro `String`typ odkazu, jako je například pole, nebo třída. Základní typ musí být typ hodnoty. Další informace naleznete [v tématu Typy hodnot a typy odkazů](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Použití proměnné typu s možnou hodnotou Null

Nejdůležitější členy typu hodnoty s možnou <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> hodnotou s možnou hodnotou jsou jeho a vlastnosti. Pro proměnnou typu hodnoty s <xref:System.Nullable%601.HasValue%2A> možnou hodnotou s možnou hodnotou s hodnotou s hodnou hodnotou se dozvíte, zda proměnná obsahuje definovanou hodnotu. Pokud <xref:System.Nullable%601.HasValue%2A> `True`je , můžete číst <xref:System.Nullable%601.Value%2A>hodnotu z . Všimněte <xref:System.Nullable%601.HasValue%2A> si, že oba a <xref:System.Nullable%601.Value%2A> jsou `ReadOnly` vlastnosti.

### <a name="default-values"></a>Výchozí hodnoty

Když deklarujete proměnnou s <xref:System.Nullable%601.HasValue%2A> hodnotou s `False`hodnotou s hodnotou s hodnotou s hodnotou s hodnotou null, její vlastnost má výchozí hodnotu . To znamená, že proměnná nemá ve výchozím nastavení žádnou definovanou hodnotu namísto výchozí hodnoty jejího základního typu hodnoty. V následujícím příkladu `numberOfChildren` proměnná zpočátku nemá žádnou definovanou `Integer` hodnotu, i když výchozí hodnota typu je 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Hodnota null je užitečná k označení nedefinované nebo neznámé hodnoty. Pokud `numberOfChildren` by byla `Integer`deklarována jako , neexistovala by žádná hodnota, která by mohla naznačovat, že informace nejsou v současné době k dispozici.

### <a name="storing-values"></a>Ukládání hodnot

Hodnotu uložte do proměnné nebo vlastnosti typu hodnoty s možnou hodnotou s možnou hodnotou. Následující příklad přiřadí hodnotu `numberOfChildren` proměnné deklarované v předchozím příkladu.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Pokud proměnná nebo vlastnost typu hodnoty s možnou hodnotou s možnou hodnotou null obsahuje definovanou hodnotu, můžete způsobit, že se vrátí do původního stavu, kdy nemá přiřazenou hodnotu. To lze provést nastavením proměnné `Nothing`nebo vlastnosti na , jak ukazuje následující příklad.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> I když `Nothing` můžete přiřadit proměnné typu hodnoty s možnou `Nothing` hodnotou, kterou lze použít pomocí rovnítku. Porovnání, které používá `someVar = Nothing`znaménko `Nothing`rovná se , vždy vyhodnotí na . Můžete <xref:System.Nullable%601.HasValue%2A> otestovat vlastnost proměnné `False`pro , nebo `Is` test `IsNot` pomocí operátoru nebo.

### <a name="retrieving-values"></a>Načítání hodnot

Chcete-li načíst hodnotu proměnné typu hodnoty s možnou hodnotou s možnou hodnotou, měli byste nejprve otestovat její <xref:System.Nullable%601.HasValue%2A> vlastnost a potvrdit, že má hodnotu. Pokud se pokusíte číst <xref:System.Nullable%601.HasValue%2A> `False`hodnotu, když <xref:System.InvalidOperationException> je , Visual Basic vyvolá výjimku. Následující příklad ukazuje doporučený způsob čtení `numberOfChildren` proměnné předchozích příkladů.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Porovnání typů s možnou hodnotou Null

Pokud jsou `Boolean` v logických výrazech použity proměnné `True`s `False`možnou hodnotou null, může být výsledkem , nebo `Nothing`. Následuje tabulka pravdy `And` pro `Or`a . Protože `b1` `b2` a nyní mají tři možné hodnoty, existuje devět kombinací k vyhodnocení.

|b1|B2|b1 A b2|b1 nebo b2|
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

Pokud je `Nothing`hodnota boolean proměnné nebo výrazu `true` , `false`není ani ani . Představte si následující příklad.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

V tomto `b1 And b2` příkladu `Nothing`vyhodnotí . V důsledku toho `Else` je klauzule `If` provedena v každém příkazu a výstup je následující:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`a `OrElse`, které používají zkrat hodnocení, musí vyhodnotit jejich druhé `Nothing`operandy, když první vyhodnotí na .

## <a name="propagation"></a>Šíření

Pokud jeden nebo oba operandy operace aritmetiky, porovnání, shift nebo typu je typ s hodnotou s možnou hodnotou s hodnotou s možnou hodnotou, je výsledkem operace také typ hodnoty s možnou hodnotou s možnou hodnotou s možnou hodnotou. Pokud oba operandy mají `Nothing`hodnoty, které nejsou , operace se provádí na základní hodnoty operandů, jako by ani byl typ hodnoty s možnou hodnotou s hodnotou. V následujícím příkladu `compare1` proměnné `sum1` a jsou implicitně zadány. Pokud na ně položíte ukazatel myši, uvidíte, že kompilátor odvodí typy hodnot s možnou hodnotou s možnou hodnotou pro oba.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Pokud jeden nebo oba operandy `Nothing`mají hodnotu `Nothing`, bude výsledkem .

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Použití typů s hodnotou Null s daty

Databáze je jedním z nejdůležitějších míst pro použití typů hodnot s možnou hodnotou s možnou hodnotou. Ne všechny databázové objekty aktuálně podporují typy hodnot s možnou hodnotou null, ale adaptéry tabulky generované návrhářem. Viz [Podpora tableadapter pro typy s možnou hodnotou null](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Viz také

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
- [Typy hodnot s hodnotou s hodnotou null (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
