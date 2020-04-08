---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888164"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo a TextElementEnumerator jsou nyní kompatibilní s UAX29

Před touto změnou <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> a <xref:System.Globalization.StringInfo?displayProperty=fullName> nesprávně zpracovat všechny clustery grafeme. Některé grafémy byly rozděleny do jejich základních složek, místo aby byly drženy pohromadě. Nyní <xref:System.Globalization.StringInfo> a <xref:System.Globalization.TextElementEnumerator> zpracujte grafeme clustery podle nejnovější verze standardu Unicode.

Kromě toho <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, která obrátí znaky v řetězci v jazyce Visual Basic, nyní také následuje standard Unicode pro clustery grafeme.

#### <a name="change-description"></a>Popis změny

Cluster [grafeme](https://www.unicode.org/glossary/#grapheme) nebo [rozšířený grafeme](https://www.unicode.org/glossary/#extended_grapheme_cluster) je jeden uživatelem vnímaný znak, který se může shodovat s více body kódu Unicode. Například řetězec obsahující thajský znak "kam" (:::no-loc text="กำ":::) se skládá z následujících dvou znaků:

- :::no-loc text="ก":::(= '\u0e01') THAJSKÝ ZNAK KO KAI
- :::no-loc text=" ำ":::(= '\u0e33') THAJSKÝ ZNAK SARA AM

Při zobrazení uživateli, operační systém kombinuje dva znaky tvořit jeden znak zobrazení (nebo grafém) "kam" nebo :::no-loc text="กำ":::. Emoji se také může skládat z více znaků, které jsou kombinovány pro zobrazení podobným způsobem.

> [!TIP]
> Dokumentace .NET někdy používá termín "textový prvek" při odkazování na grafém.

<xref:System.Globalization.StringInfo> Třídy <xref:System.Globalization.TextElementEnumerator> a kontrolují řetězce a vracejí informace o grafemích, které obsahují. V rozhraní .NET Framework (všechny verze) a .NET Core 3.x a starší, tyto dvě třídy používají vlastní logiku, která zpracovává některé kombinování tříd, ale není plně v souladu se [standardem Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries). Například <xref:System.Globalization.StringInfo> a <xref:System.Globalization.TextElementEnumerator> třídy nesprávně rozdělit jeden thajský znak "kam" zpět do jeho součásti namísto jejich udržování pohromadě. Tyto třídy také nesprávně rozdělit znak emoji "🤷🏽 ♀️" do čtyř clusterů (osoba pokrčil rameny, modifikátor tónu pleti, modifikátor pohlaví a neviditelný kombinátor) namísto jejich udržování pohromadě jako jeden grafeme clusteru.

Počínaje .NET 5, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> a třídy implementovat standard Unicode, jak je definováno [Unicode Standard \#Příloha 29, rev. 35, s. 3](https://www.unicode.org/reports/tr29/tr29-35.html). Zejména nyní vrátí [rozšířené grafeme clustery](https://www.unicode.org/glossary/#extended_grapheme_cluster) pro všechny kombinující třídy.

Zvažte následující kód jazyka C#:

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

V rozhraní .NET Framework a .NET Core 3.x a starších verzích jsou grafeme rozděleny a výstup konzoly je následující:

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

V rozhraní .NET 5 a novějších verzích jsou grafeme udržovány pohromadě a výstup konzoly je následující:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Kromě toho počínaje .NET <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 5, metoda, která obrátí znaky v řetězci v jazyce Visual Basic, nyní také následuje standard Unicode pro clustery grafeme.

Tyto změny jsou součástí širší sady vylepšení Unicode a UTF-8 v rozhraní .NET, včetně rozšířeného rozhraní API pro výčet clusteru grafeme, které doplňuje rozhraní API pro výčet skalární hodnoty Unicode, která byla zavedena s typem <xref:System.Text.Rune?displayProperty=fullName> v rozhraní .NET Core 3.0.

#### <a name="version-introduced"></a>Zavedená verze

.NET 5.0 Náhled 1

### <a name="recommended-action"></a>Doporučená akce

Nemusíte nic dělat. Vaše aplikace se budou automaticky chovat v různých scénářích souvisejících s globalizací, které budou více kompatibilní se standardy.

### <a name="category"></a>Kategorie

Globalizace

### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
