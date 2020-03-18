---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568180"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Vlastní instance EncoderFallbackBuffer nemohou rekurzivně ustoupit

Vlastní <xref:System.Text.EncoderFallbackBuffer> instance nelze rekurzivně ustoupit. Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek pořadí znaků, které je konvertibilní k cílovému kódování. V opačném případě dojde k výjimce.

#### <a name="change-description"></a>Popis změny

Během operace překódování znak-bajt, runtime detekuje špatně vytvořené nebo nekonvertibilní Sekvence UTF-16 a poskytuje tyto znaky <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody. Metoda `Fallback` určuje, které znaky by měly být nahrazeny původní nekonvertibilní data a tyto znaky jsou vyprázdněny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.

Runtime se pak pokusí překódovat tyto substituční znaky do cílového kódování. Pokud tato operace proběhne úspěšně, runtime pokračuje v překódování z místa, kde skončil v původním vstupním řetězci.

V .NET Core Preview 7 a staršíverze <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vlastní implementace můžete vrátit sekvence znaků, které nejsou konvertibilní k cílovékódování. Pokud nahrazené znaky nelze překódovat na cílové kódování, runtime <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> vyvolá metodu znovu s <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> náhradní znaky, očekává, že metoda vrátí novou substituční sekvenci. Tento proces pokračuje, dokud runtime nakonec vidí dobře tvarované, konvertibilní nahrazení, nebo dokud není dosaženo maximálního počtu rekurzí.

Počínaje rozhraním .NET Core 3.0 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí vlastní implementace aplikace vrátit sekvence znaků, které jsou konvertibilní k cílovému kódování. Pokud nahraditelné znaky nelze překódovat na cílové <xref:System.ArgumentException> kódování, je vyvolána. Runtime již nebude provádět rekurzivní volání <xref:System.Text.EncoderFallbackBuffer> do instance.

Toto chování platí pouze v případě, že jsou splněny všechny tři následující podmínky:

- Runtime detekuje špatně formátované Sekvence UTF-16 nebo UTF-16 sekvence, které nelze převést na cílové kódování.
- Byl <xref:System.Text.EncoderFallback> zadán vlastní.
- Vlastní <xref:System.Text.EncoderFallback> pokusí nahradit nové špatně vytvořené nebo nekonvertibilní UTF-16 sekvence.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Většina vývojářů nemusí provádět žádnou akci.

Pokud aplikace používá <xref:System.Text.EncoderFallback> vlastní <xref:System.Text.EncoderFallbackBuffer> a třídy, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ujistěte se, že implementace naplní záložní vyrovnávací paměti s dobře formátované <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> UTF-16 data, která je přímo konvertibilní na cílové kódování při metodě je poprvé vyvolána runtime.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
