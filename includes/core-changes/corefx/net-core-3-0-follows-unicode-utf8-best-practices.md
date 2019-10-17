---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237328"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3,0 dodržuje osvědčené postupy Unicode při nahrazování chybových sekvencí s chybou ve formátu UTF-8.

<xref:System.Text.UTF8Encoding> Když třída narazí na nesprávně vytvořenou sekvenci bajtů UTF-8 během operace překódování typu Byte-Character, nahradí tuto sekvenci znakem '�' (U + FFFD náhradní znak) ve výstupním řetězci. .NET Core 3,0 se liší od předchozích verzí rozhraní .NET Core a .NET Framework podle osvědčeného postupu Unicode pro provádění této náhrady během operace překódování.

Toto je část větší snahy o zlepšení zpracování UTF-8 v rámci .NET, včetně nových typů <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> a <xref:System.Text.Rune?displayProperty=nameWithType>. Typ <xref:System.Text.UTF8Encoding> byl dán vylepšeným způsobem zpracování chyb, aby vygeneroval výstup konzistentní s nově představenými typy.

#### <a name="change-description"></a>Změnit popis

Počínaje rozhraním .NET Core 3,0, při překódování bajtů do znaků, třída <xref:System.Text.UTF8Encoding> provádí substituci znaků na základě osvědčených postupů Unicode. Použití náhradního mechanismu je popsané [standardem Unicode verze 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v hlavičce s názvem _U + FFFD nahrazením maximálního počtu částí_.

Toto chování se vztahuje _jenom_ v případě, že vstupní bajtová sekvence obsahuje nesprávně vytvořená data UTF-8. Kromě toho, pokud byla instance <xref:System.Text.UTF8Encoding> vytvořená pomocí `throwOnInvalidBytes: true` (viz dokumentace k konstruktoru UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, instance `UTF8Encoding` se bude i nadále vyvolávat na neplatném vstupu, místo aby bylo možné provést nahrazení U + FFFD.

Následující příklad ukazuje dopad této změny s neplatným 3 bajty vstupu:

|Nesprávně vytvořený 3 bajtový vstup|Výstup před .NET Core 3,0|Výstup od .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]` (výstup dvou znaků)| `[ FFFD FFFD FFFD ]` (výstup 3 znaky)|

Tento 3 znakový výstup je preferovaný výstup podle _tabulky 3-9_ dříve propojeného PDF standardu Unicode.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

V rámci vývojáře není vyžadována žádná akce.

#### <a name="category"></a>Category

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
