---
title: Hodnoty Null (F#)
description: 'Zjistěte, jak se používá hodnota null v programovací jazyk F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 8d302cc78c5de582f58c6f9b9dea7b23ee7ddfea
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="null-values"></a>Hodnoty Null

Toto téma popisuje, jak se používá hodnota null v jazyce F #.


## <a name="null-value"></a>Hodnoty Null
Hodnota null není obvykle používá v F # pro hodnoty nebo proměnné. Hodnota null se však zobrazí jako neobvyklé hodnota v určitých situacích. Pokud typ je definovaná v F #, null není povolená jako regulární hodnotu, pokud [allownullliteral –](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atribut se používá k typu. Pokud typ je definovaná v jiném jazyce rozhraní .NET, null je možná hodnota a když jsou spolupracuje s takového typu, F # kódu setkat hodnoty null.

Pro typ definovaný v jazyce F # a používají výhradně z F #, je jediným způsobem, jak vytvořit hodnotu null, přímo pomocí knihovny F # použití [unchecked.defaultof –](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) nebo [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Ale pro typ F #, který se používá z jinými jazyky rozhraní .NET, nebo pokud používáte tento typ pomocí rozhraní API, které není napsané v jazyce F #, jako je rozhraní .NET Framework, může dojít, hodnoty null.

Můžete použít `option` typu v F # kdy můžete použít odkaz na proměnnou s hodnotou null možné v jiném jazyce .NET. Místo null, se F # `option` typu, použijte možnost hodnotu `None` Pokud neexistuje žádný objekt. Použijte možnost hodnotu `Some(obj)` s objektem `obj` po objekt. Další informace najdete v tématu [možnosti](../options.md).

`null` – Klíčové slovo je platný – klíčové slovo v jazyce F # a budete muset používat v případě, že pracujete s rozhraní API technologie .NET Framework nebo jiná rozhraní API, které jsou napsané v jiném jazyce .NET. Dvě situace, ve kterých může být nutné hodnotu null jsou při volání rozhraní API .NET a předejte hodnotu null jako argument, a při interpretovat návratovou hodnotu nebo výstupní parametr z volání metody rozhraní .NET.

Chcete metoda .NET předat hodnotu null, použijte `null` – klíčové slovo v kódu volání. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Interpretace hodnotu null, který byl získán z metody rozhraní .NET, použijte porovnávání vzorů, pokud je to možné. Následující příklad kódu ukazuje, jak použít porovnávání vzorů interpretovat hodnotu null, která je vrácena z `ReadLine` při pokusu o čtení za koncem vstupního datového proudu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Hodnoty Null pro typy F # lze generovat také jinými způsoby, například při použití `Array.zeroCreate`, který volá `Unchecked.defaultof`. Musíte být opatrní s takový kód, aby zapouzdřené hodnotami null. V knihovně určena pouze pro F # nemáte zkontrolujte hodnoty null v každé funkci. Pokud píšete knihovna pro spolupráci s jinými jazyky rozhraní .NET, možná budete muset přidat kontroluje null vstupní parametry a výjimku `ArgumentNullException`, stejně jako v kódu jazyka C# nebo Visual Basic.

Následující kód slouží ke kontrole, pokud je libovolná hodnota je null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Viz také
[Hodnoty](index.md)

[Výrazy shody](../match-expressions.md)
