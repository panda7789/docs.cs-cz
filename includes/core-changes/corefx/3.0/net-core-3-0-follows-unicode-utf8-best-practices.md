---
ms.openlocfilehash: becae23cd810623bbb33c693b707c2d4735aeece
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158466"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="bd508-101">Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="bd508-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="bd508-102">Když <xref:System.Text.UTF8Encoding> třída narazí na nesprávně vytvořenou sekvenci bajtů UTF-8 během operace překódování typu Byte-Character, nahradí tuto sekvenci znakem (U + FFFD náhradní znak) ve výstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="bd508-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="bd508-103">.NET Core 3,0 se liší od předchozích verzí rozhraní .NET Core a .NET Framework podle osvědčeného postupu Unicode pro provádění této náhrady během operace překódování.</span><span class="sxs-lookup"><span data-stu-id="bd508-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="bd508-104">Toto je část větší snahy o zlepšení zpracování UTF-8 v rámci .NET, včetně nových <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> typů a. <xref:System.Text.Rune?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bd508-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="bd508-105">Byl <xref:System.Text.UTF8Encoding> tento typ dán lepším způsobem zpracování chyb, aby byl výstup konzistentní s nově zavedený typy.</span><span class="sxs-lookup"><span data-stu-id="bd508-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bd508-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="bd508-106">Change description</span></span>

<span data-ttu-id="bd508-107">Počínaje .NET Core 3,0, při překódování bajtů na znaky, <xref:System.Text.UTF8Encoding> třída provádí substituci znaků na základě osvědčených postupů Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd508-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="bd508-108">Použití náhradního mechanismu je popsané [standardem Unicode verze 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) v hlavičce s názvem _U + FFFD nahrazením maximálního počtu částí_.</span><span class="sxs-lookup"><span data-stu-id="bd508-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="bd508-109">Toto chování se vztahuje _jenom_ v případě, že vstupní bajtová sekvence obsahuje nesprávně vytvořená data UTF-8.</span><span class="sxs-lookup"><span data-stu-id="bd508-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="bd508-110">Kromě toho, pokud <xref:System.Text.UTF8Encoding> instance byla vytvořena pomocí `throwOnInvalidBytes: true`, `UTF8Encoding` instance bude pokračovat v vyvolání neplatného vstupu místo provedení nahrazení u + FFFD.</span><span class="sxs-lookup"><span data-stu-id="bd508-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="bd508-111">Další informace o `UTF8Encoding` konstruktoru naleznete v tématu <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span><span class="sxs-lookup"><span data-stu-id="bd508-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="bd508-112">Následující tabulka ilustruje dopad této změny s neplatným 3 bajty vstupu:</span><span class="sxs-lookup"><span data-stu-id="bd508-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="bd508-113">Nesprávně vytvořený 3 bajtový vstup</span><span class="sxs-lookup"><span data-stu-id="bd508-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="bd508-114">Výstup před .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="bd508-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="bd508-115">Výstup od .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="bd508-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="bd508-116">`[ FFFD FFFD ]`(2 – výstup znaku)</span><span class="sxs-lookup"><span data-stu-id="bd508-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="bd508-117">`[ FFFD FFFD FFFD ]`(výstup 3 znaky)</span><span class="sxs-lookup"><span data-stu-id="bd508-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="bd508-118">Výstup 3-Char je preferovaný výstup podle _tabulky 3-9_ dříve propojeného PDF standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd508-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bd508-119">Představená verze</span><span class="sxs-lookup"><span data-stu-id="bd508-119">Version introduced</span></span>

<span data-ttu-id="bd508-120">3.0</span><span class="sxs-lookup"><span data-stu-id="bd508-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bd508-121">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="bd508-121">Recommended action</span></span>

<span data-ttu-id="bd508-122">V rámci vývojáře není vyžadována žádná akce.</span><span class="sxs-lookup"><span data-stu-id="bd508-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="bd508-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="bd508-123">Category</span></span>

<span data-ttu-id="bd508-124">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="bd508-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bd508-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd508-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
