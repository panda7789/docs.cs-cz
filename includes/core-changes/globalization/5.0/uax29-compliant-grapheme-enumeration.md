---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702298"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo a TextElementEnumerator jsou nyní kompatibilní s UAX29

Před touto změnou se <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> neúspěšně zpracovaly všechny clustery grapheme. Některé graphemes byly rozdělené do jejich prvků, místo aby se udržovaly dohromady. Nyní <xref:System.Globalization.StringInfo> a <xref:System.Globalization.TextElementEnumerator> zpracujte clustery grapheme podle nejnovější verze standardu Unicode.

Kromě toho <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, která převrácení znaků v řetězci v Visual Basic, teď také dodržuje standard Unicode pro clustery grapheme.

#### <a name="change-description"></a>Popis změny

Cluster [grapheme](https://www.unicode.org/glossary/#grapheme) nebo [Extended grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) je jedním uživatelem vnímaným znakem, který může být tvořen více body kódu Unicode. Například řetězec obsahující thajské znak "kam" ( :::no-loc text="กำ"::: ) se skládá z následujících dvou znaků:

- :::no-loc text="ก"::: (= ' \u0e01 ') THAJSKÉ ZNAKY KO KAI
- :::no-loc text=" ำ"::: (= ' \u0e33 ') KHMERSKÝ ZNAK SARA AM

Při zobrazení uživateli operační systém kombinuje dva znaky, aby tvořily jeden znak zobrazení (neboli grapheme) "kam" nebo :::no-loc text="กำ"::: . Emoji může také obsahovat více znaků, které jsou kombinovány pro zobrazení podobným způsobem.

> [!TIP]
> Dokumentace rozhraní .NET někdy používá termín "textový prvek" při odkazování na grapheme.

<xref:System.Globalization.StringInfo>Třídy a <xref:System.Globalization.TextElementEnumerator> kontrolují řetězce a vracejí informace o graphemes, které obsahují. V .NET Framework (všechny verze) a .NET Core 3. x a starší tyto dvě třídy používají vlastní logiku, která zpracovává některé kombinování tříd, ale plně nedodržuje [Standard Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries). <xref:System.Globalization.StringInfo>Třídy a například nesprávně rozdělují <xref:System.Globalization.TextElementEnumerator> jeden thajské znak "kam" zpátky na své součásti, namísto jejich vzájemného rozdělení. Tyto třídy také nesprávně rozdělují znak Emoji "🤷🏽 ♀️" do čtyř clusterů (osoba shrugging, modifikátor tónu skinu, modifikátor pohlaví a neviditelná kombinovaná) místo toho, aby se zachovaly jako jeden cluster grapheme.

Počínaje rozhraním .NET 5 <xref:System.Globalization.StringInfo> třídy a <xref:System.Globalization.TextElementEnumerator> implementují Standard Unicode, jak je definován [standardem Unicode Standard přílohy \# 29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html). Konkrétně teď vracejí [Rozšířené clustery grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) pro všechny kombinované třídy.

Vezměte v úvahu následující kód jazyka C#:

```cs
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

V .NET Framework a .NET Core 3. x a dřívějších verzích jsou graphemes rozdělené a výstup konzoly je následující:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

V rozhraní .NET 5 a novějších verzích se graphemes udržuje společně a výstup konzoly je následující:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Kromě toho, počínaje rozhraním .NET 5, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, která převrácení znaků v řetězci v Visual Basic, teď také dodržuje standard Unicode pro clustery grapheme.

Tyto změny jsou součástí širší sady vylepšení Unicode a UTF-8 v rozhraní .NET, včetně rozhraní API rozšířeného grapheme clusteru, které doplňují rozhraní API výčtu skalárních hodnot v kódování Unicode, které byly představeny s <xref:System.Text.Rune?displayProperty=fullName> typem v .NET Core 3,0.

#### <a name="version-introduced"></a>Představená verze

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Doporučená akce

Nemusíte provádět žádnou akci. Vaše aplikace se automaticky budou chovat v různých scénářích odpovídajících standardům, které jsou kompatibilní s globalizací.

#### <a name="category"></a>Kategorie

Globalizace

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
