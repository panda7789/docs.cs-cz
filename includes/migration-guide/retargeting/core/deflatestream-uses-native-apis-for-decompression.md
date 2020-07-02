---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614485"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="fa2fe-101">DeflateStream používá nativní rozhraní API pro dekompresi</span><span class="sxs-lookup"><span data-stu-id="fa2fe-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="fa2fe-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fa2fe-102">Details</span></span>

<span data-ttu-id="fa2fe-103">Počínaje .NET Framework 4.7.2 se implementace dekomprese ve `T:System.IO.Compression.DeflateStream` třídě změnila tak, aby ve výchozím nastavení používala nativní rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="fa2fe-104">Obvykle to vede k výraznému zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="fa2fe-105">Všechny aplikace .NET cílené na .NET Framework verze 4.7.2 nebo vyšší používají nativní implementaci. Tato změna může mít za následek určité rozdíly v chování, mezi které patří:</span><span class="sxs-lookup"><span data-stu-id="fa2fe-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="fa2fe-106">Zprávy výjimek se mohou lišit.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-106">Exception messages may be different.</span></span> <span data-ttu-id="fa2fe-107">Typ vyvolané výjimky však zůstává stejný.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="fa2fe-108">Některé zvláštní situace, jako je například nedostatek paměti k dokončení operace, mohou být zpracovány jinak.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="fa2fe-109">Existují známé rozdíly pro analýzu hlavičky gzip (Poznámka: `GZipStream` je ovlivněna pouze sada pro dekompresi):</span><span class="sxs-lookup"><span data-stu-id="fa2fe-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="fa2fe-110">Výjimky při analýze neplatných hlaviček mohou být vyvolány v různých časech.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="fa2fe-111">Nativní implementace vynucuje, že hodnoty pro některé vyhrazené příznaky v hlavičce gzip (tj. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) jsou nastaveny podle specifikace, což může způsobit výjimku, pokud byly dříve neplatné hodnoty ignorovány.</span><span class="sxs-lookup"><span data-stu-id="fa2fe-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fa2fe-112">Návrh</span><span class="sxs-lookup"><span data-stu-id="fa2fe-112">Suggestion</span></span>

<span data-ttu-id="fa2fe-113">Pokud dekomprese s nativními rozhraními API negativně ovlivnila chování vaší aplikace, můžete tuto funkci odhlásit přidáním `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` přepínače do `runtime` části souboru app.config a nastavením na `true` :</span><span class="sxs-lookup"><span data-stu-id="fa2fe-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="fa2fe-114">Name</span><span class="sxs-lookup"><span data-stu-id="fa2fe-114">Name</span></span>    | <span data-ttu-id="fa2fe-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fa2fe-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa2fe-116">Rozsah</span><span class="sxs-lookup"><span data-stu-id="fa2fe-116">Scope</span></span>   | <span data-ttu-id="fa2fe-117">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="fa2fe-117">Minor</span></span>       |
| <span data-ttu-id="fa2fe-118">Verze</span><span class="sxs-lookup"><span data-stu-id="fa2fe-118">Version</span></span> | <span data-ttu-id="fa2fe-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="fa2fe-119">4.7.2</span></span>       |
| <span data-ttu-id="fa2fe-120">Typ</span><span class="sxs-lookup"><span data-stu-id="fa2fe-120">Type</span></span>    | <span data-ttu-id="fa2fe-121">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="fa2fe-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fa2fe-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fa2fe-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
