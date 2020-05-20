---
ms.openlocfilehash: 49041ce906ab0bb8b9482b79c44302465c4ca788
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702303"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="4b09a-101">Rozhraní API globalizace používají knihovny ICU ve Windows</span><span class="sxs-lookup"><span data-stu-id="4b09a-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="4b09a-102">.NET 5,0 a novější verze používají [mezinárodní komponenty pro knihovny Unicode (ICU)](http://site.icu-project.org/home) pro funkce globalizace při spuštění ve Windows 10 se dá 2019 Update nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="4b09a-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4b09a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="4b09a-103">Change description</span></span>

<span data-ttu-id="4b09a-104">Dříve knihovny .NET používaly rozhraní API pro [národní jazykovou podporu (NLS)](/windows/win32/intl/national-language-support) pro funkce globalizace.</span><span class="sxs-lookup"><span data-stu-id="4b09a-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="4b09a-105">Například funkce NLS byly použity k získání dat jazykové verze, jako jsou například vzory formátu data a času, porovnávání řetězců a provádění řetězcového střeva v příslušné jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="4b09a-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="4b09a-106">Pokud je aplikace spuštěná ve Windows 10, která se spouští v rozhraní .NET 5,0, 2019 může aktualizace nebo novější knihovna .NET používat rozhraní API globalizace [ICU](http://site.icu-project.org/home) .</span><span class="sxs-lookup"><span data-stu-id="4b09a-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="4b09a-107">Windows 10 může 2019 aktualizace a novější verze dodávané s nativní knihovnou ICU.</span><span class="sxs-lookup"><span data-stu-id="4b09a-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="4b09a-108">Pokud modul runtime .NET nemůže načíst ICU, místo toho použije NLS.</span><span class="sxs-lookup"><span data-stu-id="4b09a-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="4b09a-109">Tato změna byla představena ze dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="4b09a-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="4b09a-110">Aplikace mají stejné chování globalizace napříč platformami, včetně Linux, macOS a Windows.</span><span class="sxs-lookup"><span data-stu-id="4b09a-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="4b09a-111">Aplikace mohou řídit chování globalizace pomocí vlastních ICU knihoven.</span><span class="sxs-lookup"><span data-stu-id="4b09a-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4b09a-112">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4b09a-112">Version introduced</span></span>

<span data-ttu-id="4b09a-113">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="4b09a-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4b09a-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4b09a-114">Recommended action</span></span>

<span data-ttu-id="4b09a-115">V rámci vývojáře není vyžadována žádná akce.</span><span class="sxs-lookup"><span data-stu-id="4b09a-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="4b09a-116">Nicméně pokud chcete i nadále používat rozhraní API globalizace NLS, můžete nastavit přepínač za [běhu](../../../../docs/core/run-time-config/globalization.md#nls) pro vrácení tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="4b09a-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="4b09a-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4b09a-117">Category</span></span>

<span data-ttu-id="4b09a-118">Globalizace</span><span class="sxs-lookup"><span data-stu-id="4b09a-118">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b09a-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4b09a-119">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="4b09a-120">Většina typů v <xref:System.Globalization?displayProperty=fullName> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="4b09a-120">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- `T:System.Span%601`
- `T:System.String`
- `N:System.Globalization`

-->
