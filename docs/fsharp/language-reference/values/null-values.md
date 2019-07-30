---
title: Hodnoty Null
description: Přečtěte si, jak se hodnota null používá F# v programovacím jazyce.
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630813"
---
# <a name="null-values"></a>Hodnoty Null

Toto téma popisuje, jak se hodnota null používá v F#.

## <a name="null-value"></a>Hodnota null

Hodnota null se obvykle nepoužívá v F# pro hodnoty nebo proměnné. Hodnota null se ale v určitých situacích zobrazí jako neobvyklá hodnota. Pokud je definován typ v F#, hodnota null není povolena jako běžná hodnota, pokud atribut [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) není použit pro typ. Pokud je definován typ v některém jiném jazyku .NET, hodnota null je možnou hodnotou a při spolupráci s těmito typy může F# kód narazit na hodnoty null.

F# Pro typ definovaný v a používané výhradně z F#, je jediným způsobem, jak vytvořit hodnotu null pomocí F# knihovny přímo, je použít nezaškrtnuto [. DefaultOf –](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) nebo [Array. zeroCreate –](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Pro F# typ, který je použit z jiných jazyků rozhraní .NET, nebo pokud používáte tento typ s rozhraním API, které není napsáno v F#, například .NET Framework, může dojít k hodnotám null.

Můžete použít `option` typ v F# případě, kdy byste mohli použít proměnnou reference s možnou hodnotou null v jiném jazyce .NET. Namísto hodnoty null s F# `option` typem, použijte hodnotu `None` možnosti, pokud není objekt. Hodnotu `Some(obj)` možnosti použijete s objektem `obj` , když je objekt. Další informace najdete v tématu [Možnosti](../options.md). Všimněte si, že můžete i nadále `null` zabalit hodnotu do možnosti, `Some x`Pokud `x` je pro `null`. Z tohoto důvodu je důležité, abyste použili `None` , pokud je `null`hodnota.

Klíčové slovo je platné klíčové slovo v F# jazyce a je nutné ho použít při práci s rozhraními API .NET Framework nebo jinými rozhraními API, která jsou napsána v jiném jazyce rozhraní .NET. `null` Dvě situace, ve kterých může být zapotřebí hodnota null, jsou při volání rozhraní .NET API a předání hodnoty null jako argumentu a při interpretaci návratové hodnoty nebo výstupního parametru z volání metody .NET.

Chcete-li předat hodnotu null metodě .NET, stačí použít `null` klíčové slovo v kódu volajícího. Následující příklad kódu to dokládá.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Chcete-li interpretovat hodnotu null získanou z metody .NET, použijte porovnávání vzorů, pokud můžete. Následující příklad kódu ukazuje, jak použít porovnávání vzorů k interpretaci hodnoty null, která je vrácena `ReadLine` z při pokusu o čtení za koncem vstupního datového proudu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Hodnoty null pro F# typy lze také vygenerovat jinými způsoby, například při použití `Array.zeroCreate`, která volání. `Unchecked.defaultof` Abyste zachovali hodnoty null, musíte být opatrní s takovým kódem. V knihovně určené pouze pro F#není nutné kontrolovat hodnoty null v každé funkci. Pokud vytváříte knihovnu pro vzájemnou operaci s jinými jazyky rozhraní .NET, bude pravděpodobně nutné přidat kontroly pro vstupní parametry null a vyvolat `ArgumentNullException`, stejně jako v C# kódu, nebo Visual Basic.

Pomocí následujícího kódu můžete zjistit, zda je libovolná hodnota null.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Viz také:

- [Hodnoty](index.md)
- [Výrazy shody](../match-expressions.md)
