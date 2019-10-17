---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237328"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="6daed-101">.NET Core 3,0 dodržuje osvědčené postupy Unicode při nahrazování chybových sekvencí s chybou ve formátu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6daed-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="6daed-102"><xref:System.Text.UTF8Encoding> Když třída narazí na nesprávně vytvořenou sekvenci bajtů UTF-8 během operace překódování typu Byte-Character, nahradí tuto sekvenci znakem '�' (U + FFFD náhradní znak) ve výstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="6daed-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="6daed-103">.NET Core 3,0 se liší od předchozích verzí rozhraní .NET Core a .NET Framework podle osvědčeného postupu Unicode pro provádění této náhrady během operace překódování.</span><span class="sxs-lookup"><span data-stu-id="6daed-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="6daed-104">Toto je část větší snahy o zlepšení zpracování UTF-8 v rámci .NET, včetně nových typů <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> a <xref:System.Text.Rune?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6daed-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="6daed-105">Typ <xref:System.Text.UTF8Encoding> byl dán vylepšeným způsobem zpracování chyb, aby vygeneroval výstup konzistentní s nově představenými typy.</span><span class="sxs-lookup"><span data-stu-id="6daed-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6daed-106">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="6daed-106">Change description</span></span>

<span data-ttu-id="6daed-107">Počínaje rozhraním .NET Core 3,0, při překódování bajtů do znaků, třída <xref:System.Text.UTF8Encoding> provádí substituci znaků na základě osvědčených postupů Unicode.</span><span class="sxs-lookup"><span data-stu-id="6daed-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="6daed-108">Použití náhradního mechanismu je popsané [standardem Unicode verze 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v hlavičce s názvem _U + FFFD nahrazením maximálního počtu částí_.</span><span class="sxs-lookup"><span data-stu-id="6daed-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="6daed-109">Toto chování se vztahuje _jenom_ v případě, že vstupní bajtová sekvence obsahuje nesprávně vytvořená data UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6daed-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="6daed-110">Kromě toho, pokud byla instance <xref:System.Text.UTF8Encoding> vytvořená pomocí `throwOnInvalidBytes: true` (viz dokumentace k konstruktoru UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, instance `UTF8Encoding` se bude i nadále vyvolávat na neplatném vstupu, místo aby bylo možné provést nahrazení U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="6daed-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="6daed-111">Následující příklad ukazuje dopad této změny s neplatným 3 bajty vstupu:</span><span class="sxs-lookup"><span data-stu-id="6daed-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="6daed-112">Nesprávně vytvořený 3 bajtový vstup</span><span class="sxs-lookup"><span data-stu-id="6daed-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="6daed-113">Výstup před .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="6daed-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="6daed-114">Výstup od .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="6daed-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="6daed-115">`[ FFFD FFFD ]` (výstup dvou znaků)</span><span class="sxs-lookup"><span data-stu-id="6daed-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="6daed-116">`[ FFFD FFFD FFFD ]` (výstup 3 znaky)</span><span class="sxs-lookup"><span data-stu-id="6daed-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="6daed-117">Tento 3 znakový výstup je preferovaný výstup podle _tabulky 3-9_ dříve propojeného PDF standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="6daed-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6daed-118">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6daed-118">Version introduced</span></span>

<span data-ttu-id="6daed-119">3.0</span><span class="sxs-lookup"><span data-stu-id="6daed-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6daed-120">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6daed-120">Recommended action</span></span>

<span data-ttu-id="6daed-121">V rámci vývojáře není vyžadována žádná akce.</span><span class="sxs-lookup"><span data-stu-id="6daed-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="6daed-122">Category</span><span class="sxs-lookup"><span data-stu-id="6daed-122">Category</span></span>

<span data-ttu-id="6daed-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6daed-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6daed-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6daed-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
