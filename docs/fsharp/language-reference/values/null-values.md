---
title: Hodnoty Null
description: 'Přečtěte si, jak se hodnota null používá v programovacím jazyce F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 3b2c7ebe7b8eff08f7c3e76b9715ccab1bbd5d36
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558345"
---
# <a name="null-values"></a>Hodnoty Null

Toto téma popisuje, jak se hodnota null používá v F #.

## <a name="null-value"></a>Hodnota null

Hodnota null se běžně nepoužívá v F # pro hodnoty nebo proměnné. Hodnota null se ale v určitých situacích zobrazí jako neobvyklá hodnota. Pokud je typ definován v jazyce F #, hodnota null není povolena jako běžná hodnota, pokud atribut [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) není použit pro typ. Pokud je definován typ v některém jiném jazyku .NET, hodnota null je možnou hodnotou a při spolupráci s těmito typy může kód F # narazit na hodnoty null.

Pro typ definovaný v F #, který se používá výhradně z F #, je jediným způsobem, jak vytvořit hodnotu null pomocí knihovny F # přímo, použít [nezaškrtnuto. DefaultOf –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) nebo [Array. zeroCreate –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate). Pro typ F #, který se používá z jiných jazyků rozhraní .NET, nebo pokud používáte tento typ s rozhraním API, které není zapsáno v F #, například .NET Framework, může dojít k hodnotám null.

Můžete použít `option` typ v F # při použití referenční proměnné s možnou hodnotou null v jiném jazyku .NET. Namísto hodnoty null s typem F # `option` použijete hodnotu možnosti, `None` Pokud není k dispozici žádný objekt. Hodnotu možnosti použijete `Some(obj)` s objektem, `obj` když je objekt. Další informace najdete v tématu [Možnosti](../options.md). Všimněte si, že můžete i nadále zabalit `null` hodnotu do možnosti, pokud je pro `Some x` `x` `null` . Z tohoto důvodu je důležité, abyste použili, `None` Pokud je hodnota `null` .

`null`Klíčové slovo je platné klíčové slovo v jazyce F # a je nutné ho použít při práci s rozhraními api .NET Framework nebo jinými rozhraními API, která jsou napsána v jiném jazyce rozhraní .NET. Dvě situace, ve kterých může být zapotřebí hodnota null, jsou při volání rozhraní .NET API a předání hodnoty null jako argumentu a při interpretaci návratové hodnoty nebo výstupního parametru z volání metody .NET.

Chcete-li předat hodnotu null metodě .NET, stačí použít `null` klíčové slovo v kódu volajícího. Následující příklad kódu to dokládá.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Chcete-li interpretovat hodnotu null získanou z metody .NET, použijte porovnávání vzorů, pokud můžete. Následující příklad kódu ukazuje, jak použít porovnávání vzorů k interpretaci hodnoty null, která je vrácena z `ReadLine` při pokusu o čtení za koncem vstupního datového proudu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Hodnoty null pro typy F # lze také vygenerovat jinými způsoby, například při použití `Array.zeroCreate` , která volání `Unchecked.defaultof` . Abyste zachovali hodnoty null, musíte být opatrní s takovým kódem. V knihovně určené pouze pro jazyk F # není nutné kontrolovat hodnoty null v každé funkci. Pokud vytváříte knihovnu pro vzájemnou operaci s jinými jazyky .NET, bude pravděpodobně nutné přidat kontroly pro vstupní parametry null a vyvolat `ArgumentNullException` , stejně jako v jazyce C# nebo Visual Basic kódu.

Pomocí následujícího kódu můžete zjistit, zda je libovolná hodnota null.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Viz také

- [Hodnoty](index.md)
- [Výrazy shody](../match-expressions.md)
