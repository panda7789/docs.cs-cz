---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888164"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="783f5-101">StringInfo a TextElementEnumerator jsou nyní kompatibilní s UAX29</span><span class="sxs-lookup"><span data-stu-id="783f5-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="783f5-102">Před touto změnou <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> a <xref:System.Globalization.StringInfo?displayProperty=fullName> nesprávně zpracovat všechny clustery grafeme.</span><span class="sxs-lookup"><span data-stu-id="783f5-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="783f5-103">Některé grafémy byly rozděleny do jejich základních složek, místo aby byly drženy pohromadě.</span><span class="sxs-lookup"><span data-stu-id="783f5-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="783f5-104">Nyní <xref:System.Globalization.StringInfo> a <xref:System.Globalization.TextElementEnumerator> zpracujte grafeme clustery podle nejnovější verze standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="783f5-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="783f5-105">Kromě toho <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, která obrátí znaky v řetězci v jazyce Visual Basic, nyní také následuje standard Unicode pro clustery grafeme.</span><span class="sxs-lookup"><span data-stu-id="783f5-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="783f5-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="783f5-106">Change description</span></span>

<span data-ttu-id="783f5-107">Cluster [grafeme](https://www.unicode.org/glossary/#grapheme) nebo [rozšířený grafeme](https://www.unicode.org/glossary/#extended_grapheme_cluster) je jeden uživatelem vnímaný znak, který se může shodovat s více body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="783f5-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="783f5-108">Například řetězec obsahující thajský znak "kam" (:::no-loc text="กำ":::) se skládá z následujících dvou znaků:</span><span class="sxs-lookup"><span data-stu-id="783f5-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="783f5-109">:::no-loc text="ก":::(= '\u0e01') THAJSKÝ ZNAK KO KAI</span><span class="sxs-lookup"><span data-stu-id="783f5-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="783f5-110">:::no-loc text=" ำ":::(= '\u0e33') THAJSKÝ ZNAK SARA AM</span><span class="sxs-lookup"><span data-stu-id="783f5-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="783f5-111">Při zobrazení uživateli, operační systém kombinuje dva znaky tvořit jeden znak zobrazení (nebo grafém) "kam" nebo :::no-loc text="กำ":::.</span><span class="sxs-lookup"><span data-stu-id="783f5-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="783f5-112">Emoji se také může skládat z více znaků, které jsou kombinovány pro zobrazení podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="783f5-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="783f5-113">Dokumentace .NET někdy používá termín "textový prvek" při odkazování na grafém.</span><span class="sxs-lookup"><span data-stu-id="783f5-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="783f5-114"><xref:System.Globalization.StringInfo> Třídy <xref:System.Globalization.TextElementEnumerator> a kontrolují řetězce a vracejí informace o grafemích, které obsahují.</span><span class="sxs-lookup"><span data-stu-id="783f5-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="783f5-115">V rozhraní .NET Framework (všechny verze) a .NET Core 3.x a starší, tyto dvě třídy používají vlastní logiku, která zpracovává některé kombinování tříd, ale není plně v souladu se [standardem Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="783f5-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="783f5-116">Například <xref:System.Globalization.StringInfo> a <xref:System.Globalization.TextElementEnumerator> třídy nesprávně rozdělit jeden thajský znak "kam" zpět do jeho součásti namísto jejich udržování pohromadě.</span><span class="sxs-lookup"><span data-stu-id="783f5-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="783f5-117">Tyto třídy také nesprávně rozdělit znak emoji "🤷🏽 ♀️" do čtyř clusterů (osoba pokrčil rameny, modifikátor tónu pleti, modifikátor pohlaví a neviditelný kombinátor) namísto jejich udržování pohromadě jako jeden grafeme clusteru.</span><span class="sxs-lookup"><span data-stu-id="783f5-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="783f5-118">Počínaje .NET 5, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> a třídy implementovat standard Unicode, jak je definováno [Unicode Standard \#Příloha 29, rev. 35, s. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="783f5-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="783f5-119">Zejména nyní vrátí [rozšířené grafeme clustery](https://www.unicode.org/glossary/#extended_grapheme_cluster) pro všechny kombinující třídy.</span><span class="sxs-lookup"><span data-stu-id="783f5-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="783f5-120">Zvažte následující kód jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="783f5-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="783f5-121">V rozhraní .NET Framework a .NET Core 3.x a starších verzích jsou grafeme rozděleny a výstup konzoly je následující:</span><span class="sxs-lookup"><span data-stu-id="783f5-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="783f5-122">V rozhraní .NET 5 a novějších verzích jsou grafeme udržovány pohromadě a výstup konzoly je následující:</span><span class="sxs-lookup"><span data-stu-id="783f5-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="783f5-123">Kromě toho počínaje .NET <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 5, metoda, která obrátí znaky v řetězci v jazyce Visual Basic, nyní také následuje standard Unicode pro clustery grafeme.</span><span class="sxs-lookup"><span data-stu-id="783f5-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="783f5-124">Tyto změny jsou součástí širší sady vylepšení Unicode a UTF-8 v rozhraní .NET, včetně rozšířeného rozhraní API pro výčet clusteru grafeme, které doplňuje rozhraní API pro výčet skalární hodnoty Unicode, která byla zavedena s typem <xref:System.Text.Rune?displayProperty=fullName> v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="783f5-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="783f5-125">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="783f5-125">Version introduced</span></span>

<span data-ttu-id="783f5-126">.NET 5.0 Náhled 1</span><span class="sxs-lookup"><span data-stu-id="783f5-126">.NET 5.0 Preview 1</span></span>

### <a name="recommended-action"></a><span data-ttu-id="783f5-127">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="783f5-127">Recommended action</span></span>

<span data-ttu-id="783f5-128">Nemusíte nic dělat.</span><span class="sxs-lookup"><span data-stu-id="783f5-128">You don't need to take any action.</span></span> <span data-ttu-id="783f5-129">Vaše aplikace se budou automaticky chovat v různých scénářích souvisejících s globalizací, které budou více kompatibilní se standardy.</span><span class="sxs-lookup"><span data-stu-id="783f5-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

### <a name="category"></a><span data-ttu-id="783f5-130">Kategorie</span><span class="sxs-lookup"><span data-stu-id="783f5-130">Category</span></span>

<span data-ttu-id="783f5-131">Globalizace</span><span class="sxs-lookup"><span data-stu-id="783f5-131">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="783f5-132">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="783f5-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
