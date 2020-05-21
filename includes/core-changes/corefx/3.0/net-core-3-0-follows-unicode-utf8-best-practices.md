---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720981"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a>Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode

Když <xref:System.Text.UTF8Encoding> Třída narazí na nesprávně vytvořenou sekvenci bajtů UTF-8 během operace překódování typu Byte-Character, nahradí tuto sekvenci znakem (U + FFFD náhradní znak) ve výstupním řetězci. .NET Core 3,0 se liší od předchozích verzí rozhraní .NET Core a .NET Framework podle osvědčeného postupu Unicode pro provádění této náhrady během operace překódování.

Toto je část větší snahy o zlepšení zpracování UTF-8 v rámci .NET, včetně nových <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> typů a. <xref:System.Text.UTF8Encoding>Byl tento typ dán lepším způsobem zpracování chyb, aby byl výstup konzistentní s nově zavedený typy.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Core 3,0, při překódování bajtů na znaky, <xref:System.Text.UTF8Encoding> třída provádí substituci znaků na základě osvědčených postupů Unicode. Použití náhradního mechanismu je popsané [standardem Unicode verze 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v hlavičce s názvem _U + FFFD nahrazením maximálního počtu částí_.

Toto chování se vztahuje _jenom_ v případě, že vstupní bajtová sekvence obsahuje nesprávně vytvořená data UTF-8. Kromě toho, pokud <xref:System.Text.UTF8Encoding> instance byla vytvořena pomocí `throwOnInvalidBytes: true` , `UTF8Encoding` instance bude pokračovat v vyvolání neplatného vstupu místo provedení nahrazení u + FFFD. Další informace o `UTF8Encoding` konstruktoru naleznete v tématu <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> .

Následující tabulka ilustruje dopad této změny s neplatným 3 bajty vstupu:

| Nesprávně vytvořený 3 bajtový vstup | Výstup před .NET Core 3,0          | Výstup od .NET Core 3,0        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | `[ FFFD FFFD ]`(2 – výstup znaku) | `[ FFFD FFFD FFFD ]`(výstup 3 znaky) |

Výstup 3-Char je preferovaný výstup podle _tabulky 3-9_ dříve propojeného PDF standardu Unicode.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

V rámci vývojáře není vyžadována žádná akce.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
