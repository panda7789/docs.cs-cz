---
title: Hodnoty Null
description: Zjistěte, jak se používá hodnotu null v F# programovací jazyk.
ms.date: 03/22/2019
ms.openlocfilehash: 93ac48eddf36981b9df550e76405c3175ae92e0a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409637"
---
# <a name="null-values"></a>Hodnoty Null

Toto téma popisuje použití hodnoty null v F#.

## <a name="null-value"></a>Hodnota Null

Hodnota null se obvykle nepoužívá F# hodnot nebo proměnné. Hodnota null se však zobrazí neobvyklé hodnoty v určitých situacích. Pokud je typ definován ve F#, null není povolena jako hodnotu regulární, není-li [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atributu se použije k typu. Pokud je typ definován v nějakém jiném jazyce .NET, null je možné hodnoty, a při interoperabilitě se u těchto typů, vaše F# kódu může dojít hodnoty null.

Pro typ definovaný v F# a slouží výhradně z F#, jedině k vytvoření hodnoty null pomocí F# knihovny je přímo použít [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) nebo [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Ale pro F# typ, který se používá od jiných jazyků .NET, nebo pokud při použití tohoto typu se rozhraní API, která není zapsána v F#, jako je například rozhraní .NET Framework, může dojít, hodnoty null.

Můžete použít `option` zadejte F# může při použití proměnné odkazu s hodnotou null je to možné v jiném jazyce .NET. Místo null pomocí F# `option` typ, použijte hodnotu možnosti `None` Pokud neexistuje žádný objekt. Použijte hodnotu možnosti `Some(obj)` s objektem `obj` po objektu. Další informace najdete v tématu [možnosti](../options.md). Všimněte si, že se můžete stále aktualizací Service pack `null` hodnoty do možnost if, pro `Some x`, `x` je `null`. Z toho důvodu je důležité, můžete použít `None` po hodnotu `null`.

`null` – Klíčové slovo je platný – klíčové slovo v F# jazyk a je nutné ho používat při práci se rozhraní API .NET Framework nebo jiná rozhraní API, které jsou napsané v jiném jazyce .NET. Dvě situace, ve kterých je třeba hodnotu null jsou při volání rozhraní API .NET a předat hodnotu null jako argument a při interpretaci návratová hodnota nebo výstupní parametr z volání metody rozhraní .NET.

Chcete metodu .NET předat hodnotu null, použijte `null` – klíčové slovo ve volajícím kódu. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Interpretace hodnotu null, která se získá z metody rozhraní .NET, použijte porovnávání vzorů, pokud je to možné. Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro interpretaci hodnotu null, která je vrácena z `ReadLine` při pokusu o čtení za koncem vstupního datového proudu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Hodnoty pro Null F# typů může být také generovány jinými způsoby, například při použití `Array.zeroCreate`, který volá `Unchecked.defaultof`. Musíte být opatrní při takový kód, aby se hodnoty null, zapouzdřené používání. V knihovně určena pouze pro F#, není potřeba zkontrolovat hodnoty null v každé funkci. Pokud vytváříte knihovnu pro spolupráci s jinými jazyky .NET, bude pravděpodobně nutné přidat kontroly hodnoty null vstupní parametry a vyvolávají `ArgumentNullException`, stejně jako v kódu C# nebo Visual Basic.

Následující kód můžete použít ke kontrole, pokud je libovolná hodnota je null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Viz také:

- [Hodnoty](index.md)
- [Výrazy shody](../match-expressions.md)
