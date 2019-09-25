---
ms.openlocfilehash: 0795ee244bf3d1261bbe61dc0c67c3936f427f04
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216335"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3,0 dodržuje osvědčené postupy Unicode při nahrazování chybových sekvencí s chybou ve formátu UTF-8.

<xref:System.Text.UTF8Encoding> Když třída narazí na nesprávně vytvořenou sekvenci bajtů UTF-8 během operace překódování typu Byte-Character, nahradí tuto sekvenci znakem "" (U + FFFD náhradní znak) ve výstupním řetězci. .NET Core 3,0 se liší od předchozích verzí rozhraní .NET Core a .NET Framework podle osvědčeného postupu Unicode pro provádění této náhrady během operace překódování.

Toto je část větší snahy o zlepšení zpracování UTF-8 v rámci .NET, včetně nových <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> typů a. <xref:System.Text.Rune?displayProperty=nameWithType> Byl <xref:System.Text.UTF8Encoding> tento typ dán lepším způsobem zpracování chyb, aby byl výstup konzistentní s nově zavedený typy.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Core 3,0, při překódování bajtů na znaky, <xref:System.Text.UTF8Encoding> třída provádí substituci znaků na základě osvědčených postupů Unicode. Použití náhradního mechanismu je popsané [standardem Unicode verze 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v hlavičce s názvem _U + FFFD nahrazením maximálního počtu částí_.

Toto chování se vztahuje _jenom_ v případě, že vstupní bajtová sekvence obsahuje nesprávně vytvořená data UTF-8. Kromě toho, pokud <xref:System.Text.UTF8Encoding> instance byla vytvořena pomocí `throwOnInvalidBytes: true` (viz dokumentace [UTF8Encoding konstruktoru třídy] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>), instance `UTF8Encoding` bude i nadále vyvolána na neplatném vstupu, nikoli provádět U + FFFD nahrazení.

Následující příklad ukazuje dopad této změny s neplatným 3 bajty vstupu:

|Nesprávně vytvořený 3 bajtový vstup|Výstup před .NET Core 3,0|Výstup od .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(2 – výstup znaku)| `[ FFFD FFFD FFFD ]`(výstup 3 znaky)|

Tento 3 znakový výstup je preferovaný výstup podle _tabulky 3-9_ dříve propojeného PDF standardu Unicode.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

V rámci vývojáře není vyžadována žádná akce.

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
