---
title: Úvod do kódování znaků v rozhraní .NET
description: Přečtěte si o kódování a dekódování znaků v rozhraní .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 85349e1e1c4eca4dd3ef7980f48350a4145fca24
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599864"
---
# <a name="character-encoding-in-net"></a>Kódování znaků v rozhraní .NET

Tento článek poskytuje Úvod k systémům kódování znaků, které používá .NET. Článek vysvětluje, jak <xref:System.String> typy, <xref:System.Char> , <xref:System.Text.Rune> a <xref:System.Globalization.StringInfo> fungují s kódováním Unicode, UTF-16 a UTF-8.

Tento *znak* se používá zde v obecném smyslu, *co čtenář detekuje jako jeden prvek zobrazení*. Běžnými příklady jsou písmena "a", symbol "@" a Emoji " 🐂 ". V některých případech se zdá, že jeden znak se ve skutečnosti skládá z několika nezávislých prvků zobrazení, protože vysvětluje oddíl [grapheme clusterů](#grapheme-clusters) .

## <a name="the-string-and-char-types"></a>stringTypy a char

Instance [string](xref:System.String) třídy představuje nějaký text. `string`Je logicky sekvencí 16bitových hodnot, z nichž každá je instancí [char](xref:System.Char) struktury. Rozhraní [ string . Vlastnost length](xref:System.String.Length) vrátí počet `char` instancí `string` instance.

Následující ukázková funkce vytiskne hodnoty v šestnáctkovém zápisu všech `char` instancí v `string` :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

Předat string "Hello" této funkci a získáte následující výstup:

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

Každý znak je reprezentován jedinou `char` hodnotou. Tento model má pro většinu jazyků světa hodnotu true. Zde je například výstup pro dva čínské znaky, jako je například *nǐ hǎo* a střední hodnota *Hello*:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

U některých jazyků a pro některé symboly a Emoji ale přebírá `char` jeden znak pomocí dvou instancí. Porovnejte například znaky a `char` instance ve slově, které znamenají *Osage* v Osage jazyce:

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

V předchozím příkladu každý znak s výjimkou prostoru je reprezentován dvěma `char` instancemi.

Jedna Emoji Unicode je také zastoupena dvěma `char` s, jak je vidět v následujícím příkladu, který ukazuje Ox Emoji:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Tyto příklady ukazují, že hodnota `string.Length` , která označuje počet `char` instancí, nemusí nutně označovat počet zobrazených znaků. Jedna `char` instance sama o sobě nutně reprezentuje znak.

`char`Páry, které jsou mapovány na jeden znak, se nazývají *náhradní páry*. Pro pochopení, jak fungují, je nutné pochopit kódování Unicode a UTF-16.

## <a name="unicode-code-points"></a>Body kódu Unicode

Unicode je mezinárodní standard kódování pro použití na různých platformách a v různých jazycích a skriptech.

Standard Unicode definuje více než 1 100 000 [kódových bodů](https://www.unicode.org/glossary/#code_point). Bod kódu je celočíselná hodnota, která může být v rozsahu od 0 do `U+10FFFF` (desítková 1 114 111). Některé body kódu jsou přiřazeny k písmenům, symbolům nebo emoji. Jiné jsou přiřazeny k akcím, které řídí způsob zobrazení textu nebo znaků, jako je například přechod na nový řádek. Mnoho bodů kódu ještě není přiřazeno.

Zde jsou některé příklady přiřazení bodů kódu s odkazy na grafy sady Unicode, ve kterých se zobrazují:

|Desetinné číslo|Soustavy       |Příklad|Popis|
|------:|----------|-------|-----------|
|10     | `U+000A` |Není k dispozici| [ČÁROVÝ KANÁL](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [MALÉ PÍSMENO LATINKY A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [VELKÉ PÍSMENO LATINKY Y S POMLČKOU](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68 675 | `U+10C43`| 𐱃 | [STARÉ ORKHONOVÉ DOPISY V](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127 801| `U+1F339`| 🌹 | [RŮŽE – Emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Body kódu jsou obvykle označovány pomocí syntaxe `U+xxxx` , kde `xxxx` je celočíselně zakódovaná celočíselná hodnota.

V celém rozsahu kódových bodů existují dva podrozsahy:

* **Základní vícejazyčné roviny (BMP)** v rozsahu `U+0000..U+FFFF` . Tento 16bitový rozsah poskytuje 65 536 kódových bodů, které jsou dostatečně k pokrytí většiny systémů pro psaní světa.
* **Doplňkové body kódu** v rozsahu `U+10000..U+10FFFF` . Tento 21. rozsah poskytuje více než milion dalších kódových bodů, které lze použít pro méně známé jazyky a jiné účely, jako je například emoji.

Následující diagram znázorňuje vztah mezi BMP a doplňkovými body kódu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP a doplňkové kódové body":::

## <a name="utf-16-code-units"></a>Jednotky kódu UTF-16

16bitový formát transformace Unicode ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) je systém kódování znaků, který používá 16bitové *jednotky kódu* pro reprezentaci bodů kódu Unicode. Rozhraní .NET používá UTF-16 ke kódování textu v `string` . `char`Instance představuje 16bitové jednotky kódu.

Jedna 16bitová jednotka kódu může představovat libovolný bod kódu v 16bitovém rozsahu základní vícejazyčné roviny. Ale pro bod kódu v doplňkovém rozsahu `char` jsou potřeba dvě instance.

## <a name="surrogate-pairs"></a>Náhradní páry

Překlad 2 16 hodnot na jednu hodnotu na 21 bitů usnadňuje speciální rozsah nazvaný *body náhrady*, od `U+D800` do `U+DFFF` (desítková 55 296 až 57 343) včetně.

Následující diagram znázorňuje vztah mezi BMP a náhradními body kódu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP a náhradní body kódu":::

Pokud je za klíčovým bodem *vysoké náhrady* `U+D800..U+DBFF` okamžitě následován bod *nízkého náhrady* ( `U+DC00..U+DFFF` ), je pár interpretován jako doplňkový bod kódu pomocí následujícího vzorce:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Toto je stejný vzorec pomocí desítkového zápisu:

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

*Vysoký* náhradní bod kódu nemá vyšší číselnou hodnotu než bod *nedostatku* náhradního kódu. Vysoký náhradní bod kódu se nazývá "vysoká", protože se používá k výpočtu vyššího řádu 11 bitů plného rozsahu 21-bitového bodu kódu. Nízká náhrada za bod kódu se používá k výpočtu 10 bitů s nižším pořadím.

Například skutečný bod kódu, který odpovídá náhradnímu páru `0xD83C` a `0xDF39` je vypočítán následujícím způsobem:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Toto je stejný výpočet pomocí desítkového zápisu:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

Předchozí příklad ukazuje, že `"\ud83c\udf39"` je kódování UTF-16 výše `U+1F339 ROSE ('🌹')` zmíněného bodu kódu.

## <a name="unicode-scalar-values"></a>Skalární hodnoty Unicode

Pojem [skalární hodnota Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) odkazuje na všechny body kódu, než jsou body náhradního kódu. Jinými slovy, skalární hodnota je jakýkoliv bod kódu, ke kterému je přiřazen znak nebo může být v budoucnu přiřazen znak. "Znak" tady odkazuje na cokoli, co může být přiřazeno k bodu kódu, který obsahuje takové věci jako akce, které řídí způsob zobrazení textu nebo znaků.

Následující diagram znázorňuje body kódu skalární hodnoty.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skalární hodnoty":::

### <a name="the-rune-type-as-a-scalar-value"></a>RuneTyp jako skalární hodnota

Počínaje rozhraním .NET Core 3,0 <xref:System.Text.Rune?displayProperty=fullName> Typ představuje skalární hodnotu Unicode. **`Rune`není k dispozici v rozhraní .NET Core 2. x nebo .NET Framework 4. x.**

`Rune`Konstruktory ověřují, zda je výsledná instance platnou skalární hodnotou kódování Unicode, jinak vyvolá výjimku. Následující příklad ukazuje kód, který úspěšně vytvoří instanci `Rune` instance, protože vstup představuje platné skalární hodnoty:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

Následující příklad vyvolá výjimku, protože bod kódu je v rozsahu nahrazení a není součástí náhradního páru:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

Následující příklad vyvolá výjimku, protože bod kódu je mimo doplňkový rozsah:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a>RunePříklad použití: Změna malých písmen

Rozhraní API, které přijímá `char` a předpokládá, že pracuje s bodem kódu, který je skalární hodnota, nefunguje správně, pokud `char` je z náhradního páru. Zvažte například následující metodu, která volá <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> každou char v string :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

Pokud `input` string obsahuje písmeno Deseret s malým písmenem `er` ( `𐑉` ), tento kód ho nepřevede na velká písmena ( `𐐡` ). Kód volá `char.ToUpperInvariant` samostatně na každý náhradní bod kódu `U+D801` a `U+DC49` . Nemá ale `U+D801` dostatek informací, aby ho identifikoval jako malé písmeno, takže `char.ToUpperInvariant` ho ponechá samostatně. A zpracovává `U+DC49` se stejným způsobem. Výsledkem je, že malé písmeno ' 𐑉 ' v ' `input` string nebude převedeno na velká písmena ' 𐑉 '.

Tady jsou dvě možnosti pro správné převádění string na velká písmena:

* Zavolejte <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na vstup string místo iterace `char` -by- `char` . `string.ToUpperInvariant`Metoda má přístup k oběma částem každého náhradního páru, takže může správně zpracovat všechny body kódu Unicode.
* Iterujte pomocí skalárních hodnot Unicode jako `Rune` instancí namísto `char` instancí, jak je znázorněno v následujícím příkladu. Vzhledem k `Rune` tomu, že instance je platná skalární hodnota Unicode, může být předána rozhraním API, která očekávají, že budou pracovat na skalární hodnotě. Například volání, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> jak je znázorněno v následujícím příkladu, poskytuje správné výsledky:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a>Další Rune rozhraní API

`Rune`Typ zveřejňuje analogové typy mnoha `char` rozhraní API. Například následující metody zrcadlí statická rozhraní API pro daný `char` Typ:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Chcete-li získat nezpracovanou skalární hodnotu z `Rune` instance, použijte <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> vlastnost.

Chcete-li převést `Rune` instanci zpět na sekvenci `char` s, použijte <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> metodu nebo <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> .

Vzhledem k tomu, že jakákoli skalární hodnota Unicode je reprezentována jedním `char` nebo náhradním párem, `Rune` může být libovolná instance reprezentovaná ve většině dvou `char` instancí. Použijte <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> k zobrazení, kolik `char` instancí je potřeba k reprezentaci `Rune` instance.

Další informace o typu .NET najdete v referenčních informacích k `Rune` [ `Rune` rozhraní API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Clustery Grapheme

To, co vypadá jako jeden znak, může být výsledkem kombinace více bodů kódu, takže výstižnější pojem, který se často používá místo "Character" je [cluster grapheme](https://www.unicode.org/glossary/#grapheme_cluster). Ekvivalentní termín v .NET je [textový prvek](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Vezměte v úvahu `string` instance "a", "á". "á" a " `👩🏽‍🚒` ". Pokud je operační systém zpracuje podle standardu Unicode, každá z těchto `string` instancí se zobrazí jako jeden textový prvek nebo grapheme cluster. Ale poslední dva jsou reprezentovány více než jedním skalárním bodem kódu.

* string"A" je reprezentován jednou skalární hodnotou a obsahuje jednu `char` instanci.

  * `U+0061 LATIN SMALL LETTER A`

* string"Á" je reprezentován jednou skalární hodnotou a obsahuje jednu `char` instanci.

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* string"Á" vypadá stejně jako "á", ale je reprezentován dvěma skalárními hodnotami a obsahuje dvě `char` instance.

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Nakonec string "" představují `👩🏽‍🚒` čtyři skalární hodnoty a obsahují sedm `char` instancí.

  * `U+1F469 WOMAN`(doplňkový rozsah, vyžaduje náhradní pár)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(doplňkový rozsah, vyžaduje náhradní pár)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(doplňkový rozsah, vyžaduje náhradní pár)

V některých předchozích příkladech, například v kombinaci s modifikátorem akcent nebo v modifikátoru intonace skinu, se bod kódu na obrazovce nezobrazí jako samostatný prvek. Místo toho slouží k úpravě vzhledu textového prvku, který byl dodán před ním. Tyto příklady ukazují, že může trvat více skalárních hodnot, aby se zajistilo, co si myslíte jako s jedním "znakem" nebo "grapheme cluster".

Chcete-li vytvořit výčet clusterů grapheme v nástroji `string` , použijte <xref:System.Globalization.StringInfo> třídu, jak je znázorněno v následujícím příkladu. Pokud jste obeznámeni s SWIFT, typ .NET `StringInfo` je koncepčně podobný [ `character` typu SWIFT](https://developer.apple.com/documentation/swift/character).

### <a name="example-count-char-rune-and-text-element-instances"></a>Příklad: počet char Rune instancí elementu text

V rozhraní .NET API se cluster grapheme nazývá *textový prvek*. Následující metoda ukazuje rozdíly mezi `char` `Rune` instancemi prvků textu, a v `string` :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Pokud tento kód spustíte v .NET Framework nebo .NET Core 3,1 nebo starším, zobrazí se počet prvků textu pro Emoji `4` . To je způsobeno chybou ve `StringInfo` třídě, která je opravena v rozhraní .NET 5.

### <a name="example-splitting-string-instances"></a>Příklad: rozdělení string instancí

Při rozdělování `string` instancí se nerozdělují náhradní páry a grapheme clustery. Vezměte v úvahu následující příklad nesprávného kódu, který má za následek vložení konců řádků každých 10 znaků v string :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Vzhledem k tomu, že tento kód vytváří výčet instancí, je náhradní pár, který je považován za překrytí `char` 10 `char` hranic, rozdělen a mezi nimi bude vložen nový řádek. Toto vložení zavádí poškození dat, protože náhradní body kódu jsou smysluplné jenom jako páry.

Možnost poškození dat není při vytváření výčtu `Rune` instancí (skalárních hodnot) namísto `char` instancí odstraněna. Sada `Rune` instancí může vytvořit cluster grapheme, který přechází na 10 `char` hranici. Pokud je sada clusterů grapheme rozdělená, nedá se správně interpretovat.

Lepším řešením je přerušit string počítání grapheme clusterů nebo textových prvků, jako v následujícím příkladu:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Jak bylo uvedeno dříve, ale v implementacích rozhraní .NET jiné než .NET 5, `StringInfo` může třída považovat některé clustery grapheme nesprávně.

## <a name="utf-8-and-utf-32"></a>UTF-8 a UTF-32

Předchozí části se zaměřují na UTF-16, protože to je to, co rozhraní .NET používá ke kódování `string` instancí. Pro Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) a [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)jsou k dispozici jiné systémy kódování. Tato kódování používají 8bitové jednotky kódu a 32 jednotek kódu v uvedeném pořadí.

Podobně jako UTF-16 vyžaduje UTF-8 několik jednotek kódu, které reprezentují některé skalární hodnoty Unicode. UTF-32 může představovat libovolnou skalární hodnotu v jedné 32-bitové kódové jednotce.

Tady je několik příkladů, které ukazují, jak je stejný bod kódu Unicode reprezentován v každém z těchto tří systémů kódování Unicode:

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

Jak bylo uvedeno dříve, jedna jednotka kódu UTF-16 z [náhradního páru](#surrogate-pairs) nemá smysl sám o sobě. Stejně tak jedna jednotka kódu UTF-8 nemá význam, pokud je v sekvenci dvou, tří nebo čtyř používaných k výpočtu skalární hodnoty.

### <a name="endianness"></a>Endianitou

V rozhraní .NET jednotky kódu UTF-16 string jsou uloženy v souvislé paměti jako sekvence 16bitových celých čísel ( `char` instancí). Bity jednotlivých jednotek kódu jsou rozloženy podle kódování [endian](https://en.wikipedia.org/wiki/Endianness) aktuální architektury.

V architektuře s malým počtem bitů by se string skládají z kódových bodů UTF-16 `[ D801 DCCC ]` v paměti jako bajty `[ 0x01, 0xD8, 0xCC, 0xDC ]` . V architektuře big-endian by se stejná velikost nahlásila string v paměti jako bajty `[ 0xD8, 0x01, 0xDC, 0xCC ]` .

Počítačové systémy, které vzájemně komunikují, musí souhlasit s tím, jak se data přenáší na síťový přenos. Většina síťových protokolů jako standard pro přenos textu používá UTF-8, aby nedocházelo k problémům, které by mohly nastat při komunikaci počítače big-endian s počítačem se systémem Little endian. stringBody kódu znakové sady UTF-8 `[ F0 90 93 8C ]` budou vždy reprezentovány jako bajty `[ 0xF0, 0x90, 0x93, 0x8C ]` bez ohledu na formát endian.

Chcete-li použít kódování UTF-8 pro přenos textu, aplikace .NET často používají kód podobný následujícímu příkladu:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

V předchozím příkladu metoda [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekóduje znak UTF-16 `string` zpět do série skalárních hodnot Unicode, poté tyto skalární hodnoty znovu ZAkóduje do znakové sady UTF-8 a umístí výslednou sekvenci do `byte` pole. Metoda [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) provádí opačnou transformaci a PŘEVÁDÍ pole UTF-8 `byte` na UTF-16 `string` .

> [!WARNING]
> Vzhledem k tomu, že UTF-8 je maloobchodech na internetu, může se stát, že se načtou nezpracované bajty z kabelu a data se budou považovat za, jako kdyby byla UTF-8. Měli byste ale ověřit, že je ve skutečnosti ve správném formátu. Uživatel se zlými úmysly může do vaší služby odeslat nesprávně formátovanou znakovou sadu UTF-8. Pokud s těmito daty pracujete, jako kdyby byla ve správném formátu, mohlo by dojít k chybám nebo bezpečnostním otvorům ve vaší aplikaci. Chcete-li ověřit data UTF-8, můžete použít metodu `Encoding.UTF8.GetString` , například, která provede ověření při převodu příchozích dat na `string` .

### <a name="well-formed-encoding"></a>Kódování ve správném formátu

Dobře formátované kódování Unicode je string jednotky kódu, které lze dekódovat jednoznačně a bez chyby v sekvenci skalárních hodnot Unicode. Data ve správném formátu se dají překódovat volně a zpátky mezi UTF-8, UTF-16 a UTF-32.

Otázka, zda je sekvence kódování ve správném formátu nebo nesouvisí se Endian architektury počítače. Nesprávně vytvořená sekvence UTF-8 je nesprávně vytvořená stejným způsobem na počítačích se systémem big endian a little endian.

Tady je několik příkladů nesprávně vytvořených kódování:

* V kódování UTF-8 je sekvence `[ 6C C2 61 ]` nesprávně vytvořená, protože `C2` nemůže následovat `61` .

* V kódování UTF-16 je sekvence `[ DC00 DD00 ]` (nebo v jazyce C#, a string `"\udc00\udd00"` ) nesprávně vytvořená, protože Nízká náhrada `DC00` nemůže následovat za jinou nízkou náhradou `DD00` .

* V kódování UTF-32 je sekvence `[ 0011ABCD ]` nesprávně vytvořená, protože `0011ABCD` je mimo rozsah skalárních hodnot Unicode.

V rozhraní .NET `string` instance téměř vždy obsahují dobře vytvořená data UTF-16, ale nejsou zaručena. Následující příklady znázorňují platný kód C#, který v instancích vytváří nesprávně se formátovanou data UTF-16 `string` .

* Nesprávně vytvořený literál:

  ```csharp
  const string s = "\ud800";
  ```

* Podřetězec, který rozděluje náhradní pár:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Rozhraní API [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) , jako nikdy nevracejí nesprávně formátované `string` instance. `Encoding.GetString`a `Encoding.GetBytes` metody zjišťují ve vstupní sekvenci nesprávně formátované sekvence a při generování výstupu provede substituci znaků. Například pokud se [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) ve vstupu zobrazí bajt jiného typu než ASCII (mimo rozsah U + 0000.. U + 007F), vloží do vrácené instance znak? `string` . [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)nahradí nesprávně vytvořené sekvence UTF-8 `U+FFFD REPLACEMENT CHARACTER ('�')` ve vrácené `string` instanci. Další informace najdete v části [Standard Unicode](https://www.unicode.org/versions/latest/), oddíly 5,22 a 3,9.

Vestavěné `Encoding` třídy lze také nakonfigurovat tak, aby vyvolaly výjimku, místo aby prováděla substituci znaků při výskytu chybně formátované sekvence. Tento přístup se často používá v aplikacích citlivých na zabezpečení, kde nemusí být přijatelná náhrada znaků.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Informace o použití vestavěných `Encoding` tříd naleznete v tématu [How to use Class Encoding Classes in .NET](character-encoding.md).

## <a name="see-also"></a>Viz také

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Globalizace a lokalizace](../globalization-localization/index.md)
