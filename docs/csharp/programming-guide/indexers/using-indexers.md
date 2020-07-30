---
title: Použití indexerů – Průvodce programováním v C#
description: Naučte se deklarovat a používat indexer pro třídu, strukturu nebo rozhraní v jazyce C#. Tento článek obsahuje příklad kódu.
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: a8a9e05c1d2e44841177a924c6ff51c6c9e6a05a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301863"
---
# <a name="using-indexers-c-programming-guide"></a>Použití indexerů (Průvodce programováním v C#)

Indexery jsou syntaktické pohodlí, které umožňují vytvořit [třídu](../../language-reference/keywords/class.md), [strukturu](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) , ke kterým můžou klientské aplikace přistupovat jako k poli. Kompilátor vygeneruje `Item` vlastnost (nebo případně pojmenovanou vlastnost, pokud existuje <xref:System.Runtime.CompilerServices.IndexerNameAttribute> ) a příslušné přístupové metody. Indexery se nejčastěji implementují v typech, jejichž primární účel je zapouzdření interní kolekce nebo pole. Předpokládejme například, že máte třídu `TempRecord` , která představuje teplotu ve stupních Fahrenheita zaznamenanou v 10 různých časech během 24 hodin. Třída obsahuje `temps` pole typu `float[]` pro uložení hodnot teploty. Implementací indexeru v této třídě mají klienti přístup k teplotám v instanci, `TempRecord` jako `float temp = tempRecord[4]` místo jako `float temp = tempRecord.temps[4]` . Zápis indexeru zjednodušuje syntaxi pro klientské aplikace. poskytuje také třídu a její účel intuitivnější pro jiné vývojáře, aby porozuměli.

Chcete-li deklarovat indexer pro třídu nebo strukturu, použijte klíčové slovo [This](../../language-reference/keywords/this.md) , jak ukazuje následující příklad:

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> Deklarace indexeru automaticky vygeneruje vlastnost s názvem `Item` na objektu. `Item`Vlastnost není přímo přístupná z [výrazu přístupu členů](../../language-reference/operators/member-access-operators.md#member-access-expression-)instance. Pokud navíc `Item` do objektu s indexerem přidáte vlastní vlastnost, zobrazí se [Chyba kompilátoru CS0102](../../misc/cs0102.md). Chcete-li se této chybě vyhnout, použijte příkaz <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Přejmenovat indexer, jak je popsáno níže.

## <a name="remarks"></a>Poznámky

Typ indexeru a typ jeho parametrů musí být alespoň tak přístupný jako indexovací člen. Další informace o úrovních dostupnosti najdete v tématu [modifikátory přístupu](../../language-reference/keywords/access-modifiers.md).

Další informace o použití indexerů s rozhraním naleznete v tématu [indexery rozhraní](./indexers-in-interfaces.md).

Signatura indexeru se skládá z počtu a typů jeho formálních parametrů. Nezahrnuje typ indexeru ani názvy formálních parametrů. Pokud deklarujete více než jednoho indexeru ve stejné třídě, musí mít jiné signatury.

Hodnota indexeru není klasifikována jako proměnná; Proto nemůžete předat hodnotu indexeru jako parametr [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) .

Chcete-li poskytnout indexer s názvem, který mohou použít jiné jazyky, použijte <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu:

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

Tento indexer bude mít název `TheItem` , protože ho přepíše atribut názvu indexeru. Ve výchozím nastavení je název indexeru `Item` .

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak deklarovat pole soukromého pole, `temps` a indexer. Indexer umožňuje přímý přístup k instanci `tempRecord[i]` . Alternativou k použití indexeru je deklarovat pole jako [veřejný](../../language-reference/keywords/public.md) člen a přistupovat ke svým členům, `tempRecord.temps[i]` přímo.

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

Všimněte si, že když je vyhodnocen přístup indexeru, například v `Console.Write` příkazu, je vyvolán přistupující objekt [Get](../../language-reference/keywords/get.md) . Proto pokud neexistuje žádný `get` přistupující objekt, dojde k chybě při kompilaci.

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a>Indexování pomocí jiných hodnot

C# neomezuje typ parametru indexeru na celé číslo. Může být například užitečné použít řetězec s indexerem. Takový indexer může být implementován vyhledáním řetězce v kolekci a vrácením příslušné hodnoty. V případě, že jsou přístupové objekty přetíženy, může řetězec a celočíselná verze existovat současně.

## <a name="example-2"></a>Příklad 2

Následující příklad deklaruje třídu, která ukládá dny v týdnu. `get`Přistupující objekt přebírá řetězec, název dne a vrátí odpovídající celé číslo. Například "neděle" vrátí 0, "pondělí" vrátí 1 a tak dále.

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a>Spotřebovává se příklad 2

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a>Příklad 3

Následující příklad deklaruje třídu, která ukládá dny v týdnu pomocí <xref:System.DayOfWeek?displayProperty=fullName> výčtu. `get`Přistupující objekt přebírá `DayOfWeek` hodnotu Day a vrátí odpovídající celé číslo. Například vrátí hodnotu `DayOfWeek.Sunday` 0, `DayOfWeek.Monday` vrátí 1 a tak dále.

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a>Spotřebovává se příklad 3

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a>Robustní programování

Existují dva hlavní způsoby, jak lze zlepšit zabezpečení a spolehlivost indexerů:

- Nezapomeňte začlenit nějaký typ strategie zpracování chyb pro zpracování pravděpodobnosti, že klientský kód projde neplatnou hodnotou indexu. V prvním příkladu výše v tomto tématu Třída TempRecord poskytuje vlastnost length, která umožňuje kódu klienta ověřit vstup před jeho předáním indexeru. Kód pro zpracování chyb můžete také vložit do samotného indexeru. Nezapomeňte uživatelům zdokumentovat všechny výjimky, které jste vyvolali uvnitř přístupového objektu indexeru.

- Nastavte přístupnost přístupových objektů [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) jako omezujících oprávnění, která jsou přiměřená. To je důležité pro `set` přistupující objekt, zejména. Další informace najdete v tématu [Omezení přístupnosti přístupového objektu](../classes-and-structs/restricting-accessor-accessibility.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
