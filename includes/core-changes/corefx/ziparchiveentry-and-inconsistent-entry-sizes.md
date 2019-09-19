---
ms.openlocfilehash: 748e7f484227b6a60a2309bde185079b30fe19de
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117170"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="f82e9-101">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="f82e9-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="f82e9-102">Archivy zip uvádějí komprimovanou velikost i nekomprimovanou velikost v centrálním adresáři a v místní hlavičce.</span><span class="sxs-lookup"><span data-stu-id="f82e9-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="f82e9-103">Samotná data samotného záznamu také označují jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="f82e9-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="f82e9-104">V .NET Core 2,2 a dřívějších verzích se tyto hodnoty nikdy nekontrolovaly konzistence.</span><span class="sxs-lookup"><span data-stu-id="f82e9-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="f82e9-105">Počínaje .NET Core 3,0 jsou teď.</span><span class="sxs-lookup"><span data-stu-id="f82e9-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f82e9-106">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="f82e9-106">Change description</span></span>

<span data-ttu-id="f82e9-107">V .NET Core 2,2 a starších verzích se <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> aplikace zdaří i v případě, že místní hlavička odsouhlasí s centrálním hlavičkou souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="f82e9-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="f82e9-108">Data se dekomprimuje, dokud se nedosáhne konce zkomprimovaného datového proudu, a to i v případě, že jeho délka přesáhne velikost nekomprimovaného souboru, která je uvedená v centrálním adresáři/místní hlavičce.</span><span class="sxs-lookup"><span data-stu-id="f82e9-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="f82e9-109">Počínaje rozhraním .NET Core 3,0 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> metoda kontroluje, zda se místní hlavička a centrální hlavička dohodnou na komprimovaných a nekomprimovaných velikostech položky.</span><span class="sxs-lookup"><span data-stu-id="f82e9-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="f82e9-110">Pokud ne, metoda vyvolá <xref:System.IO.InvalidDataException> výjimku, pokud místní hlavička nebo seznam popisovačů dat archivu, které nesouhlasí s centrálním adresářem souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="f82e9-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="f82e9-111">Při čtení položky se dekomprimovaná data zkrátí na nekomprimovaný soubor, který je uveden v hlavičce.</span><span class="sxs-lookup"><span data-stu-id="f82e9-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="f82e9-112">Tato změna byla provedena, aby se zajistilo, že <xref:System.IO.Compression.ZipArchiveEntry> správně představuje velikost svých dat a že je čteno pouze množství dat.</span><span class="sxs-lookup"><span data-stu-id="f82e9-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f82e9-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f82e9-113">Version introduced</span></span>

<span data-ttu-id="f82e9-114">3.0</span><span class="sxs-lookup"><span data-stu-id="f82e9-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f82e9-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f82e9-115">Recommended action</span></span>

<span data-ttu-id="f82e9-116">Znovu zabalit libovolný archiv zip, který tyto problémy vykazuje.</span><span class="sxs-lookup"><span data-stu-id="f82e9-116">Repackage any zip archive which exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="f82e9-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f82e9-117">Category</span></span>

<span data-ttu-id="f82e9-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f82e9-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f82e9-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f82e9-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`


-->

