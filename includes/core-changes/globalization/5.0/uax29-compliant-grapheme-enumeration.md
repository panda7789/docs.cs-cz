---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702298"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="0c8c0-101">StringInfo a TextElementEnumerator jsou nyní kompatibilní s UAX29</span><span class="sxs-lookup"><span data-stu-id="0c8c0-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="0c8c0-102">Před touto změnou se <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> neúspěšně zpracovaly všechny clustery grapheme.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="0c8c0-103">Některé graphemes byly rozdělené do jejich prvků, místo aby se udržovaly dohromady.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="0c8c0-104">Nyní <xref:System.Globalization.StringInfo> a <xref:System.Globalization.TextElementEnumerator> zpracujte clustery grapheme podle nejnovější verze standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="0c8c0-105">Kromě toho <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, která převrácení znaků v řetězci v Visual Basic, teď také dodržuje standard Unicode pro clustery grapheme.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0c8c0-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="0c8c0-106">Change description</span></span>

<span data-ttu-id="0c8c0-107">Cluster [grapheme](https://www.unicode.org/glossary/#grapheme) nebo [Extended grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) je jedním uživatelem vnímaným znakem, který může být tvořen více body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="0c8c0-108">Například řetězec obsahující thajské znak "kam" ( :::no-loc text="กำ"::: ) se skládá z následujících dvou znaků:</span><span class="sxs-lookup"><span data-stu-id="0c8c0-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="0c8c0-109">:::no-loc text="ก":::(= ' \u0e01 ') THAJSKÉ ZNAKY KO KAI</span><span class="sxs-lookup"><span data-stu-id="0c8c0-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="0c8c0-110">:::no-loc text=" ำ":::(= ' \u0e33 ') KHMERSKÝ ZNAK SARA AM</span><span class="sxs-lookup"><span data-stu-id="0c8c0-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="0c8c0-111">Při zobrazení uživateli operační systém kombinuje dva znaky, aby tvořily jeden znak zobrazení (neboli grapheme) "kam" nebo :::no-loc text="กำ"::: .</span><span class="sxs-lookup"><span data-stu-id="0c8c0-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="0c8c0-112">Emoji může také obsahovat více znaků, které jsou kombinovány pro zobrazení podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="0c8c0-113">Dokumentace rozhraní .NET někdy používá termín "textový prvek" při odkazování na grapheme.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="0c8c0-114"><xref:System.Globalization.StringInfo>Třídy a <xref:System.Globalization.TextElementEnumerator> kontrolují řetězce a vracejí informace o graphemes, které obsahují.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="0c8c0-115">V .NET Framework (všechny verze) a .NET Core 3. x a starší tyto dvě třídy používají vlastní logiku, která zpracovává některé kombinování tříd, ale plně nedodržuje [Standard Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="0c8c0-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="0c8c0-116"><xref:System.Globalization.StringInfo>Třídy a například nesprávně rozdělují <xref:System.Globalization.TextElementEnumerator> jeden thajské znak "kam" zpátky na své součásti, namísto jejich vzájemného rozdělení.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="0c8c0-117">Tyto třídy také nesprávně rozdělují znak Emoji "🤷🏽 ♀️" do čtyř clusterů (osoba shrugging, modifikátor tónu skinu, modifikátor pohlaví a neviditelná kombinovaná) místo toho, aby se zachovaly jako jeden cluster grapheme.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="0c8c0-118">Počínaje rozhraním .NET 5 <xref:System.Globalization.StringInfo> třídy a <xref:System.Globalization.TextElementEnumerator> implementují Standard Unicode, jak je definován [standardem Unicode Standard přílohy \# 29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="0c8c0-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="0c8c0-119">Konkrétně teď vracejí [Rozšířené clustery grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) pro všechny kombinované třídy.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="0c8c0-120">Vezměte v úvahu následující kód jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="0c8c0-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="0c8c0-121">V .NET Framework a .NET Core 3. x a dřívějších verzích jsou graphemes rozdělené a výstup konzoly je následující:</span><span class="sxs-lookup"><span data-stu-id="0c8c0-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="0c8c0-122">V rozhraní .NET 5 a novějších verzích se graphemes udržuje společně a výstup konzoly je následující:</span><span class="sxs-lookup"><span data-stu-id="0c8c0-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="0c8c0-123">Kromě toho, počínaje rozhraním .NET 5, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, která převrácení znaků v řetězci v Visual Basic, teď také dodržuje standard Unicode pro clustery grapheme.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="0c8c0-124">Tyto změny jsou součástí širší sady vylepšení Unicode a UTF-8 v rozhraní .NET, včetně rozhraní API rozšířeného grapheme clusteru, které doplňují rozhraní API výčtu skalárních hodnot v kódování Unicode, které byly představeny s <xref:System.Text.Rune?displayProperty=fullName> typem v .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c8c0-125">Představená verze</span><span class="sxs-lookup"><span data-stu-id="0c8c0-125">Version introduced</span></span>

<span data-ttu-id="0c8c0-126">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="0c8c0-126">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c8c0-127">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0c8c0-127">Recommended action</span></span>

<span data-ttu-id="0c8c0-128">Nemusíte provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-128">You don't need to take any action.</span></span> <span data-ttu-id="0c8c0-129">Vaše aplikace se automaticky budou chovat v různých scénářích odpovídajících standardům, které jsou kompatibilní s globalizací.</span><span class="sxs-lookup"><span data-stu-id="0c8c0-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

#### <a name="category"></a><span data-ttu-id="0c8c0-130">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0c8c0-130">Category</span></span>

<span data-ttu-id="0c8c0-131">Globalizace</span><span class="sxs-lookup"><span data-stu-id="0c8c0-131">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c8c0-132">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0c8c0-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
