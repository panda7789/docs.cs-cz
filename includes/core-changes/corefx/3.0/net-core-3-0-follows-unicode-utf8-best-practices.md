---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568156"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>Rozhraní .NET Core 3.0 se řídí osvědčenými postupy unicode při výměně špatně vytvořených bajtových sekvencí UTF-8

Když <xref:System.Text.UTF8Encoding> třída narazí na špatně formátované UTF-8 bajt sekvence během operace překódování bajt-znak, nahradí tuto sekvenci znakem ' ' (U + FFFD NÁHRADNÍ ZNAK) ve výstupním řetězci. .NET Core 3.0 se liší od předchozích verzí rozhraní .NET Core a rozhraní .NET Framework podle osvědčeného osvědčeného postupu unicode pro provedení této náhrady během operace překódování.

Toje součástí větší úsilí o zlepšení zpracování UTF-8 v <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> celé <xref:System.Text.Rune?displayProperty=nameWithType> .NET, včetně nové a typy. Typ <xref:System.Text.UTF8Encoding> byl dán lepší mechaniky zpracování chyb tak, aby vytváří výstup v souladu s nově zavedené typy.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Core 3.0, když překódování <xref:System.Text.UTF8Encoding> bajtů na znaky, třída provádí nahrazení znaků na základě osvědčených postupů Unicode. Použitý substituční mechanismus je popsán [standardem Unicode, verze 12.0, § 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v nadpisu s názvem _U+FFFD Substituce maximálních subdílů_.

Toto chování platí _pouze_ v případě, že vstupní bajt sekvence obsahuje špatně vytvořená data UTF-8. Navíc pokud <xref:System.Text.UTF8Encoding> instance byla vytvořena s `throwOnInvalidBytes: true` (viz [UTF8Encoding konstruktor<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>dokumentace]( , `UTF8Encoding` instance bude i nadále vyvolávat na neplatný vstup, spíše než provádět Nahrazení U + FFFD.

Následující ilustruje dopad této změny s neplatným 3bajtovým vstupem:

|Špatně vytvořený 3bajtový vstup|Výstup před rozhraním .NET Core 3.0|Výstup začínající na .NET Core 3.0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(Dvoumístný výstup)| `[ FFFD FFFD FFFD ]`(3znakový výstup)|

Tento 3-char výstup je preferovaný výstup, podle _tabulky 3-9_ dříve propojeného Unicode Standard PDF.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Není vyžadována žádná akce ze strany vývojáře.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
