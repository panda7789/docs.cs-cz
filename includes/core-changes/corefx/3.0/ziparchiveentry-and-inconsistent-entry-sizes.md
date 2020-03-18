---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568074"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="793ef-101">ZipArchiveEntry již zpracovává archivy s nekonzistentními velikostmi položek</span><span class="sxs-lookup"><span data-stu-id="793ef-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="793ef-102">Zip archivy seznam jak komprimované velikosti a nekomprimované velikosti v centrálním adresáři a místní záhlaví.</span><span class="sxs-lookup"><span data-stu-id="793ef-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="793ef-103">Vstupní data sama také označuje jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="793ef-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="793ef-104">V rozhraní .NET Core 2.2 a starších verzích nebyly tyto hodnoty nikdy kontrolovány na konzistenci.</span><span class="sxs-lookup"><span data-stu-id="793ef-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="793ef-105">Počínaje rozhraním .NET Core 3.0 nyní jsou.</span><span class="sxs-lookup"><span data-stu-id="793ef-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="793ef-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="793ef-106">Change description</span></span>

<span data-ttu-id="793ef-107">V rozhraní .NET Core 2.2 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> a starších verzích se daří i v případě, že místní záhlaví nesouhlasí s centrální záhlaví souboru zip.</span><span class="sxs-lookup"><span data-stu-id="793ef-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="793ef-108">Data jsou dekomprimována až do dosažení konce komprimovaného datového proudu, a to i v případě, že jejich délka přesahuje velikost nekomprimovaného souboru uvedenou v centrálním adresáři nebo místní hlavičce.</span><span class="sxs-lookup"><span data-stu-id="793ef-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="793ef-109">Počínaje rozhraním .NET Core <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 3.0 metoda kontroluje, zda se místní hlavička a centrální hlavička dohodnou na komprimovaných a nekomprimovaných velikostech položky.</span><span class="sxs-lookup"><span data-stu-id="793ef-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="793ef-110">Pokud tomu tak není, metoda <xref:System.IO.InvalidDataException> vyvolá pokud je místní záhlaví nebo velikosti seznamu popisovačů dat, které nesouhlasí s centrálním adresářem souboru zip.</span><span class="sxs-lookup"><span data-stu-id="793ef-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="793ef-111">Při čtení položky jsou dekomprimovaná data zkrácena na nekomprimovanou velikost souboru uvedenou v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="793ef-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="793ef-112">Tato změna byla provedena, <xref:System.IO.Compression.ZipArchiveEntry> aby bylo zajištěno, že správně představuje velikost jeho dat a že je přečteno pouze toto množství dat.</span><span class="sxs-lookup"><span data-stu-id="793ef-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="793ef-113">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="793ef-113">Version introduced</span></span>

<span data-ttu-id="793ef-114">3.0</span><span class="sxs-lookup"><span data-stu-id="793ef-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="793ef-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="793ef-115">Recommended action</span></span>

<span data-ttu-id="793ef-116">Přebalit všechny zip archiv, který vykazuje tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="793ef-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="793ef-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="793ef-117">Category</span></span>

<span data-ttu-id="793ef-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="793ef-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="793ef-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="793ef-119">Affected APIs</span></span>

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
