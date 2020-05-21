---
ms.openlocfilehash: 00c32c10f77995284264e795d386f699082dcb84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721209"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.

Vlastní <xref:System.Text.EncoderFallbackBuffer> instance nemůžou vracet rekurzivně zpátky. Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek sekvenci znaků, která je převoditelná na cílové kódování. V opačném případě dojde k výjimce.

#### <a name="change-description"></a>Popis změny

Během operace překódování znaků modul runtime detekuje nesprávně vytvořené sekvence UTF-16 a poskytuje tyto znaky <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodě. `Fallback`Metoda určuje, které znaky by měly být nahrazeny původními nepřevoditelnými daty a tyto znaky jsou vynásobeny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.

Modul runtime se pak pokusí překódovat tyto náhradní znaky do cílového kódování. Pokud tato operace proběhne úspěšně, modul runtime pokračuje v kódování z místa, kde bylo ponecháno v původním vstupním řetězci.

V .NET Core Preview 7 a starších verzích mohou vlastní implementace pro <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které nelze převést na cílové kódování. Pokud nahrazené znaky nelze překódovat do cílového kódování, modul runtime <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ihned vyvolá metodu s náhradními znaky a očekává, že <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> Metoda vrátí novou sekvenci nahrazení. Tento proces pokračuje, dokud modul runtime nakonec nenalezne dobře vytvořenou, převoditelnou substituci nebo až do dosažení maximálního počtu rekurzí.

Počínaje .NET Core 3,0, vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí vracet sekvence znaků, které jsou převoditelné na cílové kódování. Pokud nahrazené znaky nelze překódovat do cílového kódování, <xref:System.ArgumentException> je vyvolána výjimka. Modul runtime již nebude do instance volat rekurzivní volání <xref:System.Text.EncoderFallbackBuffer> .

Toto chování platí pouze v případě, že jsou splněny všechny tři z následujících podmínek:

- Modul runtime detekuje nesprávně vytvořenou sekvenci UTF-16 nebo sekvenci UTF-16, kterou nelze převést na cílové kódování.
- Byla zadána vlastní aplikace <xref:System.Text.EncoderFallback> .
- Vlastní <xref:System.Text.EncoderFallback> pokusy o náhradu nové sekvence UTF-16, která se nesprávně vytvořila nebo nepřevoditelná.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Většina vývojářů nemusí podepisovat nějakou akci.

Pokud aplikace používá vlastní <xref:System.Text.EncoderFallback> třídu a, ujistěte se, že <xref:System.Text.EncoderFallbackBuffer> implementace <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> naplní záložní vyrovnávací paměť se správnými daty UTF-16, která je přímo převoditelná na cílové kódování, když <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> je metoda poprvé vyvolána modulem runtime.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
