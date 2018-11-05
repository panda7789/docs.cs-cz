---
title: Hodnoty Null (F#)
description: 'Zjistěte, jak se v programovacím jazyce F # používá hodnotu null.'
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787894"
---
# <a name="null-values"></a>Hodnoty Null

Toto téma popisuje, jak se používá hodnotu null v jazyce F #.

## <a name="null-value"></a>Hodnota Null

Hodnotu null se obvykle nepoužívá v jazyce F # pro hodnoty nebo proměnné. Hodnota null se však zobrazí neobvyklé hodnoty v určitých situacích. Pokud je typ definován v jazyce F #, null není povolena jako hodnotu regulární, není-li [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atributu se použije k typu. Pokud je typ definován v nějakém jiném jazyce .NET, null je možná hodnota a při interoperabilitě se se službou těchto typů, kódu F # zaznamenat hodnoty null.

Pro typ definovaný v jazyce F # a používají výhradně z jazyka F #, je jediný způsob, jak vytvořit hodnotu null, přímo pomocí knihovny F # použití [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) nebo [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Však pro typ jazyka F #, který se používá z jiných jazyků .NET, nebo pokud při použití tohoto typu se rozhraní API, které nejsou napsané v jazyce F #, jako je například rozhraní .NET Framework, může dojít, hodnoty null.

Můžete použít `option` typu v jazyce F # kdy můžete použít odkaz na proměnnou s možná hodnota null v jiném jazyce .NET. Místo null pomocí jazyka F # `option` typ, použijte možnost hodnotu `None` Pokud neexistuje žádný objekt. Použijte hodnotu možnosti `Some(obj)` s objektem `obj` po objektu. Další informace najdete v tématu [možnosti](../options.md).

`null` – Klíčové slovo je platný – klíčové slovo v jazyce F # a je nutné ho používat při práci se rozhraní API .NET Framework nebo jiná rozhraní API, které jsou napsané v jiném jazyce .NET. Dvě situace, ve kterých je třeba hodnotu null jsou při volání rozhraní API .NET a předat hodnotu null jako argument a při interpretaci návratová hodnota nebo výstupní parametr z volání metody rozhraní .NET.

Chcete metodu .NET předat hodnotu null, použijte `null` – klíčové slovo ve volajícím kódu. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Interpretace hodnotu null, která se získá z metody rozhraní .NET, použijte porovnávání vzorů, pokud je to možné. Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro interpretaci hodnotu null, která je vrácena z `ReadLine` při pokusu o čtení za koncem vstupního datového proudu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Hodnoty Null u typů F # může být také generovány jinými způsoby, například při použití `Array.zeroCreate`, který volá `Unchecked.defaultof`. Musíte být opatrní při takový kód, aby se hodnoty null, zapouzdřené používání. V knihovně je určena pouze pro F # není nutné pro kontrolu hodnot null v každé funkci. Pokud vytváříte knihovnu pro spolupráci s jinými jazyky .NET, bude pravděpodobně nutné přidat kontroly hodnoty null vstupní parametry a vyvolávají `ArgumentNullException`, stejně jako v kódu C# nebo Visual Basic.

Následující kód můžete použít ke kontrole, pokud je libovolná hodnota je null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Viz také:

- [Hodnoty](index.md)
- [Výrazy shody](../match-expressions.md)
