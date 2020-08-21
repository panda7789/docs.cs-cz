---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720182"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="a3f51-101">Rozpoznání identifikátoru URI cest UNC v systému UNIX</span><span class="sxs-lookup"><span data-stu-id="a3f51-101">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="a3f51-102"><xref:System.Uri>Třída teď rozpoznává řetězce, které začínají dvěma lomítky ( `//` ) jako cesty UNC (Universal Naming Convention) v operačních systémech UNIX.</span><span class="sxs-lookup"><span data-stu-id="a3f51-102">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="a3f51-103">Tato změna způsobí, že chování pro tyto řetězce je konzistentní napříč všemi platformami.</span><span class="sxs-lookup"><span data-stu-id="a3f51-103">This change makes the behavior for such strings consistent across all platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a3f51-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a3f51-104">Change description</span></span>

<span data-ttu-id="a3f51-105">V předchozích verzích rozhraní .NET <xref:System.Uri> Třída rozpoznává řetězce, které začínají se dvěma lomítky, například `//contoso` jako absolutní cesty k souborům v operačních systémech UNIX.</span><span class="sxs-lookup"><span data-stu-id="a3f51-105">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="a3f51-106">Ve Windows se ale tyto řetězce rozpoznávají jako cesty UNC.</span><span class="sxs-lookup"><span data-stu-id="a3f51-106">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="a3f51-107">Počínaje rozhraním .NET 5,0 <xref:System.Uri> Třída rozpoznává řetězce, které začínají se dvěma lomítky jako cesty UNC na všech platformách, včetně systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="a3f51-107">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="a3f51-108">Kromě toho se vlastnosti chovají podle sémantiky UNC:</span><span class="sxs-lookup"><span data-stu-id="a3f51-108">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="a3f51-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> Vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="a3f51-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="a3f51-110">Zpětná lomítka v cestě jsou nahrazena lomítky.</span><span class="sxs-lookup"><span data-stu-id="a3f51-110">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="a3f51-111">Například `//first\second` se bude jednat o `//first/second` .</span><span class="sxs-lookup"><span data-stu-id="a3f51-111">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="a3f51-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> Nejedná se o procentuální kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="a3f51-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="a3f51-113">Například `//first/\uFFF0` není převeden na *not* `//first/%EF%BF%B0` .</span><span class="sxs-lookup"><span data-stu-id="a3f51-113">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a3f51-114">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a3f51-114">Version introduced</span></span>

<span data-ttu-id="a3f51-115">5,0</span><span class="sxs-lookup"><span data-stu-id="a3f51-115">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a3f51-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a3f51-116">Recommended action</span></span>

<span data-ttu-id="a3f51-117">V rámci vývojáře není vyžadována žádná akce.</span><span class="sxs-lookup"><span data-stu-id="a3f51-117">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="a3f51-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a3f51-118">Category</span></span>

<span data-ttu-id="a3f51-119">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="a3f51-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a3f51-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a3f51-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
