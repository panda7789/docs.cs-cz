---
title: Úvod k kódování znaků v rozhraní .NET
description: Informace o kódování a dekódování znaků v rozhraní .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134407"
---
# <a name="character-encoding-in-net"></a>Kódování znaků v rozhraní .NET

Tento článek obsahuje úvod do systémů kódování znaků, které používá rozhraní .NET. Článek <xref:System.String>vysvětluje, jak <xref:System.Char>, <xref:System.Text.Rune>, <xref:System.Globalization.StringInfo> a typy pracovat s Unicode, UTF-16 a UTF-8.

Termín *znak* se zde používá v obecném smyslu *toho, co čtenář vnímá jako jeden zobrazovací prvek*. Běžnými příklady jsou písmeno "a", symbol "@" a emoji "🐂". Někdy to, co vypadá jako jeden znak, se ve skutečnosti skládá z více nezávislých prvků zobrazení, jak vysvětluje část [grafeme clusterů.](#grapheme-clusters)

## <a name="the-string-and-char-types"></a>Typy řetězců a znaků

Instance [třídy string](xref:System.String) představuje určitý text. A `string` je logicky posloupnost 16bitových hodnot, z nichž každá je instancí třídy [char.](xref:System.Char) [Řetězec. Vlastnost Length](xref:System.String.Length) vrátí `char` počet instancí v instanci. `string`

Následující ukázková funkce vytiskne hodnoty v šestnáctkovém zápisu všech `char` `string`instancí v aplikaci :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

Předat řetězec "Hello" na tuto funkci a získáte následující výstup:

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

Každý znak je reprezentován jedinou `char` hodnotou. Tento vzorec platí pro většinu světových jazyků. Například, tady je výstup pro dva čínské znaky, které zní *Hello*jako *n?*

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Pro některé jazyky a pro některé symboly `char` a emodži však trvá dvě instance představují jeden znak. Porovnejte například `char` znaky a instance ve slově, které znamená *Osage* v jazyce Osage:

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

V předchozím příkladu je každý znak kromě `char` mezery reprezentován dvěma instancemi.

Jeden unicode emoji je také `char`reprezentován dvěma s, jak je vidět v následujícím příkladu ukazujícím vůl emoji:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Tyto příklady ukazují, `string.Length`že hodnota , `char` která označuje počet instancí, nemusí nutně označovat počet zobrazených znaků. Jedna `char` instance sama o sobě nemusí nutně představovat znak.

Dvojice, `char` které mapují na jeden znak, se nazývají *náhradní páry*. Chcete-li pochopit, jak fungují, musíte pochopit kódování Unicode a UTF-16.

## <a name="unicode-code-points"></a>Body kódu Unicode

Unicode je mezinárodní standard kódování pro použití na různých platformách a s různými jazyky a skripty.

Standard Unicode definuje více než 1,1 milionu [bodů kódu](https://www.unicode.org/glossary/#code_point). Bod kódu je celá hodnota, která může `U+10FFFF` být v rozsahu od 0 do (desetinné číslo 1 114 111). Některé body kódu jsou přiřazeny písmenům, symbolům nebo emodži. Jiné jsou přiřazeny k akcím, které řídí způsob zobrazení textu nebo znaků, například postup na nový řádek. Mnoho bodů kódu ještě není přiřazeno.

Zde jsou některé příklady přiřazení bodů kódu s odkazy na grafy Unicode, ve kterých se zobrazují:

|Desetinné číslo|Hex       |Příklad|Popis|
|------:|----------|-------|-----------|
|10     | `U+000A` |Není dostupné.| [PŘÍKON LINKY](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [MALÉ PÍSMENO LATINKy A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | V roce 201 | [Velké písmeno latinky Y s makronem](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68,675 | `U+10C43`| 𐱃 | [OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127,801| `U+1F339`| 🌹 | [ROSE emodži](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Body kódu jsou obvykle označovány pomocí `U+xxxx`syntaxe , kde `xxxx` je hex kódovaná celočíselná hodnota.

V celém rozsahu bodů kódu existují dva podrozsahy:

* **Základní vícejazyčná rovina (BMP)** v rozsahu `U+0000..U+FFFF`. Tato 16bitová řada poskytuje 65 536 bodů kódu, což je dost na pokrytí většiny světových systémů zápisu.
* **Doplňkové kódové body** `U+10000..U+10FFFF`v rozsahu . Tato 21bitová oblast poskytuje více než milion dalších bodů kódu, které lze použít pro méně známé jazyky a další účely, jako jsou emodži.

Následující diagram znázorňuje vztah mezi BMP a doplňkovými body kódu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP a doplňkové kódové body":::

## <a name="utf-16-code-units"></a>Kódové jednotky UTF-16

16bitový formát transformace Unicode ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) je systém kódování znaků, který používá 16bitové *kódové jednotky* k reprezentaci bodů kódu Unicode. Rozhraní .NET používá UTF-16 ke `string`kódování textu v rozhraní . Instance `char` představuje 16bitovou jednotku kódu.

Jedna 16bitová jednotka kódu může představovat libovolný bod kódu v 16bitovém rozsahu základní vícejazyčné roviny. Ale pro bod kódu v doplňkovéoblasti `char` jsou potřeba dvě instance.

## <a name="surrogate-pairs"></a>Náhradní páry

Překlad dvou 16bitových hodnot na jednu 21bitovou hodnotu je usnadněn `U+D800` zvláštním `U+DFFF` rozsahem nazývaným náhradní *body kódu*, z do (desetinné 55 296 až 57 343) včetně.

Následující diagram znázorňuje vztah mezi BMP a náhradní body kódu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP a náhradní kódové body":::

Pokud je bod kódu`U+D800..U+DBFF` *vysokého náhradníka* ( )`U+DC00..U+DFFF`bezprostředně následován bodem kódu *nízkého náhradního* ( ), je dvojice interpretována jako doplňkový bod kódu pomocí následujícího vzorce:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Tady je stejný vzorec s desítkovou notací:

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

Bod kódu *s vysokým* náhradním kódem nemá vyšší číselnou hodnotu než bod kódu *s nízkým* náhradním kódem. Bod kódu s vysokým náhradním kódem se nazývá "vysoká", protože se používá k výpočtu 11 bitů vyššího řádu v rozsahu bodů celého 21bitového kódu. Dolní náhradní bod kódu se používá k výpočtu nižší pořadí 10 bitů.

Například skutečný bod kódu, který odpovídá `0xD83C` náhradní `0xDF39` dvojici a vypočítá se takto:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Zde je stejný výpočet s desítkovou notací:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

Předchozí příklad ukazuje, `"\ud83c\udf39"` že je UTF-16 kódování `U+1F339 ROSE ('🌹')` bodu kódu již bylo zmíněno dříve.

## <a name="unicode-scalar-values"></a>Skalární hodnoty Unicode

Termín [Unicode skalární hodnota](https://www.unicode.org/glossary/#unicode_scalar_value) odkazuje na všechny body kódu než náhradní body kódu. Jinými slovy skalární hodnota je libovolný bod kódu, který je přiřazen znak nebo může být přiřazen znak v budoucnu. "Znak" zde odkazuje na cokoli, co lze přiřadit k bodu kódu, který zahrnuje takové věci, jako jsou akce, které řídí, jak se zobrazuje text nebo znaky.

Následující diagram znázorňuje body kódu skalární hodnoty.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skalární hodnoty":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>Typ Rune jako skalární hodnota

Počínaje rozhraním .NET Core <xref:System.Text.Rune?displayProperty=fullName> 3.0 představuje typ skalární hodnotu Unicode. **`Rune`není k dispozici v rozhraní .NET Core 2.x nebo .NET Framework 4.x.**

Konstruktory `Rune` ověřují, zda je výsledná instance platnou skalární hodnotou Unicode, jinak vyvolá výjimku. Následující příklad ukazuje kód, který úspěšně `Rune` instancije instance, protože vstup představuje platné skalární hodnoty:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

Následující příklad vyvolá výjimku, protože bod kódu je v oblasti náhradní a není součástí náhradní dvojice:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

Následující příklad vyvolá výjimku, protože bod kódu je mimo doplňkový rozsah:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Runepříklad použití: změna písmene

Rozhraní API, `char` které přebírá a předpokládá, že pracuje s bodem kódu, který je `char` skalární hodnota nefunguje správně, pokud je z náhradní pár. Zvažte například následující metodu, char která stringvolá <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> každý v :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

`input` string Pokud obsahuje malé písmeno Deseret `er` (`𐑉`), tento kód jej`𐐡`nepřevede na velká písmena ( ). Kód volá `char.ToUpperInvariant` samostatně na každém `U+D801` bodě `U+DC49`náhradního kódu a . Ale `U+D801` nemá dostatek informací sám o sobě identifikovat jako malé `char.ToUpperInvariant` písmeno, tak to nechává na pokoji. A zvládá `U+DC49` to stejně. Výsledkem je, že malá písmena "", v písmenu `input` string a) se nepřevedou na velká písmena .'.

Zde jsou dvě možnosti string pro správný převod na velká písmena:

* Volání <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na string vstup spíše než `char`iterace -by-`char`. Metoda `string.ToUpperInvariant` má přístup k oběma částem každé náhradní dvojice, takže může správně zpracovat všechny body kódu Unicode.
* Iterate prostřednictvím skalární hodnoty `Rune` Unicode `char` jako instance namísto instancí, jak je znázorněno v následujícím příkladu. Vzhledem `Rune` k tomu, že instance je platnou skalární hodnotou Unicode, může být předána do prostředí API, která očekávají, že budou pracovat s skalární hodnotou. Například volání, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> jak je znázorněno v následujícím příkladu, poskytuje správné výsledky:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>Další Rune api

Typ `Rune` zveřejňuje analogy mnoha `char` api. Například následující metody zrcadlí statická `char` api na typu:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Chcete-li získat nezpracovaná skalární hodnota z `Rune` instance, použijte <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> vlastnost.

Chcete-li `Rune` převést instanci zpět <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> na <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> posloupnost `char`s, použijte nebo metodu.

Vzhledem k tomu, že jakákoli skalární hodnota Unicode je rezivovatelná jedním `char` nebo náhradním párem, může být jakákoli `Rune` instance reprezentována maximálně 2 `char` instancemi. Slouží <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> k zobrazení, kolik `char` instancí `Rune` je nutné reprezentovat instanci.

Další informace o typu `Rune` .NET naleznete v [ `Rune` odkazu rozhraní API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Grafemové klastry

Co vypadá jako jeden znak může vyplývat z kombinace více bodů kódu, takže více popisný termín, který se často používá místo "znak" je [grafeme clusteru](https://www.unicode.org/glossary/#grapheme_cluster). Ekvivalentní termín v rozhraní .NET je [textový prvek](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Zvažte `string` instance "a", "á". "á" a`👩🏽‍🚒`" ". Pokud je operační systém zpracovává podle specifikace standardu Unicode, každá z těchto `string` instancí se zobrazí jako jeden textový prvek nebo cluster grafeme. Ale poslední dva jsou reprezentovány více než jeden skalární bod kódu hodnoty.

* string "A" je reprezentováno jednou skalární `char` hodnotou a obsahuje jednu instanci.

  * `U+0061 LATIN SMALL LETTER A`

* "Á" string je reprezentováno jednou skalární `char` hodnotou a obsahuje jednu instanci.

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* "Á" string vypadá stejně jako "á", ale je reprezentovándvěma skalárními hodnotami a obsahuje dvě `char` instance.

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Nakonec string "`👩🏽‍🚒`" je reprezentován čtyřmi skalárními hodnotami a obsahuje sedm `char` instancí.

  * `U+1F469 WOMAN`(doplňkový rozsah, vyžaduje náhradní pár)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(doplňkový rozsah, vyžaduje náhradní pár)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(doplňkový rozsah, vyžaduje náhradní pár)

V některých předchozích příkladech – například modifikátoru diakritiky nebo modifikátoru tónu pleti – se bod kódu nezobrazuje jako samostatný prvek na obrazovce. Spíše slouží k úpravě vzhledu textového prvku, který byl před ním. Tyto příklady ukazují, že může trvat více skalární hodnoty, aby se to, co si myslíme, že jako jeden "znak" nebo "grafém clusteru."

Chcete-li vytvořit výčet clusterů grafeme `string` <xref:System.Globalization.StringInfo> , použijte třídu, jak je znázorněno v následujícím příkladu. Pokud jste obeznámeni s Swift, `StringInfo` typ .NET je koncepčně podobný [ `character` typu Swift](https://developer.apple.com/documentation/swift/character).

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>Příklad: charinstance Runeelementů count , a text element

V rozhraní API rozhraní .NET se cluster grafeme nazývá *textový prvek*. Následující metoda ukazuje rozdíly mezi `char` `Rune`instancemi prvků , a `string`textového prvku v :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Pokud spustíte tento kód v rozhraní .NET Framework nebo .NET Core 3.1 nebo starší, zobrazí `4`se počet textových prvků pro emoji . To je způsobeno chybou `StringInfo` ve třídě, která je opravena v rozhraní .NET 5.

### <a name="example-splitting-opno-locstring-instances"></a>Příklad: string rozdělení instancí

Při `string` rozdělení instance, vyhnout se rozdělení náhradní páry a grafeme clustery. Vezměme si následující příklad nesprávného kódu, který má stringv úmyslu vložit zalomení řádků každých 10 znaků v :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Vzhledem k tomu, `char` že tento kód vytvoří výčet instancí,`char` náhradní pár, který se stane rozkročit hranice 10 bude rozdělena a nový řádek vložen mezi nimi. Toto vložení zavádí poškození dat, protože náhradní body kódu jsou smysluplné pouze jako páry.

Potenciál pro poškození dat není eliminován, `Rune` pokud výčet instancí `char` (skalární hodnoty) namísto instancí. Sada `Rune` instancí může vytvořit cluster grafeme, který se`char` rozkládá na hranici 10. Pokud je sada clusteru grafeme rozdělena, nelze ji správně interpretovat.

Lepším přístupem je string přerušit počítání grafeme clusterů nebo textových prvků, jako v následujícím příkladu:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Jak již bylo uvedeno dříve, však v implementacích `StringInfo` .NET než .NET 5, třída může zpracovat některé clustery grafeme nesprávně.

## <a name="utf-8-and-utf-32"></a>UTF-8 a UTF-32

Předchozí části zaměřené na UTF-16, protože to je to, `string` co rozhraní .NET používá ke kódování instancí. Existují i jiné kódovací systémy pro Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) a [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32). Tato kódování používají jednotky 8bitového kódu a jednotky 32bitového kódu.

Stejně jako UTF-16, UTF-8 vyžaduje více jednotek kódu představují některé skalární hodnoty Unicode. UTF-32 může představovat libovolnou skalární hodnotu v jedné jednotce 32bitového kódu.

Zde jsou některé příklady, které ukazují, jak je v každém z těchto tří kódovacích systémů Unicode reprezentován stejný bod kódu Unicode:

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

Jak již bylo uvedeno dříve, jeden kód UTF-16 jednotky z [náhradní pár](#surrogate-pairs) je bezvýznamný sám o sobě. Stejným způsobem jedna jednotka kódu UTF-8 je sama o sobě bezvýznamná, pokud je v posloupnosti dvou, tří nebo čtyř, která se používá k výpočtu skalární hodnoty.

### <a name="endianness"></a>Endianness

V rozhraní .NET string jsou kódové jednotky UTF-16 uloženy v souvislé paměti jako posloupnost`char` 16bitových celočísel (instancí). Bity jednotlivých kódových jednotek jsou rozloženy podle [endianness](https://en.wikipedia.org/wiki/Endianness) aktuální architektury.

Na malé endian string architektury, skládající se z Bodů kódu `[ D801 DCCC ]` UTF-16 by být stanoveny v paměti jako bajty `[ 0x01, 0xD8, 0xCC, 0xDC ]`. Na big-endian architektury, string že stejné by být stanoveny `[ 0xD8, 0x01, 0xDC, 0xCC ]`v paměti jako bajty .

Počítačové systémy, které vzájemně komunikují, se musí dohodnout na reprezentaci dat překračujících drát. Většina síťových protokolů používá UTF-8 jako standard při přenosu textu, částečně proto, aby se zabránilo problémům, které by mohly vyplývat z počítače big-endian, který komunikuje s počítačem s malým endianem. Skládání string z bodů `[ F0 90 93 8C ]` kódu UTF-8 bude vždy reprezentováno jako bajty `[ 0xF0, 0x90, 0x93, 0x8C ]` bez ohledu na endianness.

Chcete-li použít UTF-8 pro přenos textu, aplikace .NET často používají kód jako v následujícím příkladu:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

V předchozím příkladu metoda [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekóduje UTF-16 `string` zpět do řady skalárních hodnot Unicode, pak znovu zakóduje tyto skalární hodnoty `byte` do UTF-8 a umístí výslednou sekvenci do pole. Metoda [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) provádí opačnou transformaci, převod `byte` utf-8 pole `string`UTF-16 .

> [!WARNING]
> Vzhledem k tomu, UTF-8 je samozřejmostí na internetu, to může být lákavé číst syrové byty z drátu a zacházet s daty, jako by to bylo UTF-8. Měli byste však ověřit, že je skutečně dobře tvarovaný. Škodlivý klient může odeslat špatně vytvořené UTF-8 do vaší služby. Pokud pracujete s tato data, jako kdyby byly ve správném formátu, může způsobit chyby nebo bezpečnostní díry ve vaší aplikaci. Chcete-li ověřit data UTF-8, `Encoding.UTF8.GetString`můžete použít metodu, jako je , `string`která provede ověření při převodu příchozích dat na .

### <a name="well-formed-encoding"></a>Dobře formátované kódování

Dobře formátované kódování Unicode string je kódové jednotky, které lze jednoznačně a bez chybdekódovat do posloupnosti skalárních hodnot Unicode. Dobře formátovaná data mohou být volně překódována mezi UTF-8, UTF-16 a UTF-32.

Otázka, zda je sekvence kódování ve správném formátu nebo ne, nesouvisí s endianness architektury počítače. Špatně tvarovaná sekvence UTF-8 je špatně vytvořená stejným způsobem na strojích big-endian i little-endian.

Zde je několik příkladů špatně vytvořených kódování:

* V UTF-8 sekvence `[ 6C C2 61 ]` je špatně `C2` vytvořena, `61`protože nemůže být následován .

* V UTF-16 sekvence `[ DC00 DD00 ]` (nebo string `"\udc00\udd00"`v C#, ) je špatně `DC00` vytvořena, protože nízké `DD00`náhradní nemůže následovat další nízké náhradní .

* V UTF-32 sekvence `[ 0011ABCD ]` je špatně `0011ABCD` vytvořena, protože je mimo rozsah skalární hodnoty Unicode.

V rozhraní `string` .NET instance téměř vždy obsahují dobře vytvořená data UTF-16, ale to není zaručeno. Následující příklady ukazují platný kód Jazyka C#, který v `string` instancích vytváří špatně vytvořená data UTF-16.

* Špatně tvarovaný doslov:

  ```csharp
  const string s = "\ud800";
  ```

* Podřetězec, který rozdělí náhradní pár:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Api jako [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) nikdy vrátit `string` špatně vytvořené instance. `Encoding.GetString`a `Encoding.GetBytes` metody detekují špatně vytvořené sekvence ve vstupu a provádějí substituci znaků při generování výstupu. Například pokud [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) vidí non-ASCII bajt ve vstupu (mimo rozsah U + 0000..U + 007F), vloží `string` '?' do vrácené instance. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)nahradí špatně vytvořené sekvence UTF-8 ve `string` vrácené `U+FFFD REPLACEMENT CHARACTER ('�')` instanci. Další informace naleznete [v části Unicode Standard](https://www.unicode.org/versions/latest/), oddíly 5.22 a 3.9.

Předdefinované `Encoding` třídy lze také nakonfigurovat tak, aby vyvolávají výjimku, spíše než provádět nahrazení znaků, když jsou vidět špatně vytvořené sekvence. Tento přístup se často používá v aplikacích citlivých na zabezpečení, kde nahrazení znaků nemusí být přijatelné.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Informace o použití předdefinovaných `Encoding` tříd naleznete v tématu [Použití tříd kódování znaků v rozhraní .NET](character-encoding.md).

## <a name="see-also"></a>Viz také

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
