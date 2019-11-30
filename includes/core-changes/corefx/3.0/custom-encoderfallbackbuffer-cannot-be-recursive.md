---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568180"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.

Vlastní instance <xref:System.Text.EncoderFallbackBuffer> nemohou vracet rekurzivně. Implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musí mít za následek sekvenci znaků, která bude převoditelná na cílové kódování. V opačném případě dojde k výjimce.

#### <a name="change-description"></a>Změnit popis

Během operace překódování znaků modul runtime detekuje nesprávně vytvořené sekvence UTF-16 a poskytuje tyto znaky metodě <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>. Metoda `Fallback` určuje, které znaky by měly být nahrazeny původními nepřevoditelnými daty a tyto znaky jsou vynásobeny voláním <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ve smyčce.

Modul runtime se pak pokusí překódovat tyto náhradní znaky do cílového kódování. Pokud tato operace proběhne úspěšně, modul runtime pokračuje v kódování z místa, kde bylo ponecháno v původním vstupním řetězci.

V rozhraní .NET Core Preview 7 a starších verzích mohou vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které nelze převést na cílové kódování. Pokud nahrazené znaky nelze překódovat do cílového kódování, modul runtime vyvolá metodu <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> znovu s náhradními znaky a očekává, že <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metoda vrátí novou sekvenci nahrazení. Tento proces pokračuje, dokud modul runtime nakonec nenalezne dobře vytvořenou, převoditelnou substituci nebo až do dosažení maximálního počtu rekurzí.

Počínaje rozhraním .NET Core 3,0 musí vlastní implementace <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> vracet sekvence znaků, které jsou převoditelné na cílové kódování. Pokud nahrazené znaky nelze překódovat do cílového kódování, je vyvolána <xref:System.ArgumentException>. Modul runtime již nebude provádět rekurzivní volání do instance <xref:System.Text.EncoderFallbackBuffer>.

Toto chování platí pouze v případě, že jsou splněny všechny tři z následujících podmínek:

- Modul runtime detekuje nesprávně vytvořenou sekvenci UTF-16 nebo sekvenci UTF-16, kterou nelze převést na cílové kódování.
- Byl zadán vlastní <xref:System.Text.EncoderFallback>.
- Vlastní <xref:System.Text.EncoderFallback> se pokusí nahradit novou sekvenci UTF-16 ve špatném formátu nebo nepřevoditelnou.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Většina vývojářů nemusí podepisovat nějakou akci.

Pokud aplikace používá vlastní <xref:System.Text.EncoderFallback> a <xref:System.Text.EncoderFallbackBuffer> třídu, ujistěte se, že implementace <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> naplní záložní vyrovnávací paměť se správnými daty UTF-16, která je přímo převoditelná na cílové kódování, pokud je metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> poprvé vyvolána modulem runtime.

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
