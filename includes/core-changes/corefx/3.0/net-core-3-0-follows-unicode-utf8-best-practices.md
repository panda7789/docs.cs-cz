---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568156"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="b9906-101">Rozhraní .NET Core 3.0 se řídí osvědčenými postupy unicode při výměně špatně vytvořených bajtových sekvencí UTF-8</span><span class="sxs-lookup"><span data-stu-id="b9906-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="b9906-102">Když <xref:System.Text.UTF8Encoding> třída narazí na špatně formátované UTF-8 bajt sekvence během operace překódování bajt-znak, nahradí tuto sekvenci znakem ' ' (U + FFFD NÁHRADNÍ ZNAK) ve výstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="b9906-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="b9906-103">.NET Core 3.0 se liší od předchozích verzí rozhraní .NET Core a rozhraní .NET Framework podle osvědčeného osvědčeného postupu unicode pro provedení této náhrady během operace překódování.</span><span class="sxs-lookup"><span data-stu-id="b9906-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="b9906-104">Toje součástí větší úsilí o zlepšení zpracování UTF-8 v <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> celé <xref:System.Text.Rune?displayProperty=nameWithType> .NET, včetně nové a typy.</span><span class="sxs-lookup"><span data-stu-id="b9906-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="b9906-105">Typ <xref:System.Text.UTF8Encoding> byl dán lepší mechaniky zpracování chyb tak, aby vytváří výstup v souladu s nově zavedené typy.</span><span class="sxs-lookup"><span data-stu-id="b9906-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b9906-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b9906-106">Change description</span></span>

<span data-ttu-id="b9906-107">Počínaje rozhraním .NET Core 3.0, když překódování <xref:System.Text.UTF8Encoding> bajtů na znaky, třída provádí nahrazení znaků na základě osvědčených postupů Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9906-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="b9906-108">Použitý substituční mechanismus je popsán [standardem Unicode, verze 12.0, § 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v nadpisu s názvem _U+FFFD Substituce maximálních subdílů_.</span><span class="sxs-lookup"><span data-stu-id="b9906-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="b9906-109">Toto chování platí _pouze_ v případě, že vstupní bajt sekvence obsahuje špatně vytvořená data UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b9906-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="b9906-110">Navíc pokud <xref:System.Text.UTF8Encoding> instance byla vytvořena s `throwOnInvalidBytes: true` (viz [UTF8Encoding konstruktor<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>dokumentace]( , `UTF8Encoding` instance bude i nadále vyvolávat na neplatný vstup, spíše než provádět Nahrazení U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="b9906-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="b9906-111">Následující ilustruje dopad této změny s neplatným 3bajtovým vstupem:</span><span class="sxs-lookup"><span data-stu-id="b9906-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="b9906-112">Špatně vytvořený 3bajtový vstup</span><span class="sxs-lookup"><span data-stu-id="b9906-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="b9906-113">Výstup před rozhraním .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b9906-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="b9906-114">Výstup začínající na .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b9906-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="b9906-115">`[ FFFD FFFD ]`(Dvoumístný výstup)</span><span class="sxs-lookup"><span data-stu-id="b9906-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="b9906-116">`[ FFFD FFFD FFFD ]`(3znakový výstup)</span><span class="sxs-lookup"><span data-stu-id="b9906-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="b9906-117">Tento 3-char výstup je preferovaný výstup, podle _tabulky 3-9_ dříve propojeného Unicode Standard PDF.</span><span class="sxs-lookup"><span data-stu-id="b9906-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b9906-118">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="b9906-118">Version introduced</span></span>

<span data-ttu-id="b9906-119">3.0</span><span class="sxs-lookup"><span data-stu-id="b9906-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9906-120">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b9906-120">Recommended action</span></span>

<span data-ttu-id="b9906-121">Není vyžadována žádná akce ze strany vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b9906-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="b9906-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b9906-122">Category</span></span>

<span data-ttu-id="b9906-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="b9906-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9906-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b9906-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
