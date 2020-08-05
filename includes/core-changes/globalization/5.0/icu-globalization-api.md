---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302702"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="a8195-101">Rozhraní API globalizace používají knihovny ICU ve Windows</span><span class="sxs-lookup"><span data-stu-id="a8195-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="a8195-102">.NET 5,0 a novější verze používají [mezinárodní komponenty pro knihovny Unicode (ICU)](http://site.icu-project.org/home) pro funkce globalizace při spuštění ve Windows 10 se dá 2019 Update nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="a8195-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a8195-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a8195-103">Change description</span></span>

<span data-ttu-id="a8195-104">Dříve knihovny .NET používaly rozhraní API pro [národní jazykovou podporu (NLS)](/windows/win32/intl/national-language-support) pro funkce globalizace.</span><span class="sxs-lookup"><span data-stu-id="a8195-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="a8195-105">Například funkce NLS byly použity k získání dat jazykové verze, jako jsou například vzory formátu data a času, porovnávání řetězců a provádění řetězcového střeva v příslušné jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="a8195-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="a8195-106">Pokud je aplikace spuštěná ve Windows 10, která se spouští v rozhraní .NET 5,0, 2019 může aktualizace nebo novější knihovna .NET používat rozhraní API globalizace [ICU](http://site.icu-project.org/home) .</span><span class="sxs-lookup"><span data-stu-id="a8195-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="a8195-107">Windows 10 může 2019 aktualizace a novější verze dodávané s nativní knihovnou ICU.</span><span class="sxs-lookup"><span data-stu-id="a8195-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="a8195-108">Pokud modul runtime .NET nemůže načíst ICU, místo toho použije NLS.</span><span class="sxs-lookup"><span data-stu-id="a8195-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="a8195-109">Tato změna byla představena ze dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="a8195-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="a8195-110">Aplikace mají stejné chování globalizace napříč platformami, včetně Linux, macOS a Windows.</span><span class="sxs-lookup"><span data-stu-id="a8195-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="a8195-111">Aplikace mohou řídit chování globalizace pomocí vlastních ICU knihoven.</span><span class="sxs-lookup"><span data-stu-id="a8195-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8195-112">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a8195-112">Version introduced</span></span>

<span data-ttu-id="a8195-113">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="a8195-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8195-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a8195-114">Recommended action</span></span>

<span data-ttu-id="a8195-115">V rámci vývojáře není vyžadována žádná akce.</span><span class="sxs-lookup"><span data-stu-id="a8195-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="a8195-116">Nicméně pokud chcete i nadále používat rozhraní API globalizace NLS, můžete nastavit přepínač za [běhu](../../../../docs/core/run-time-config/globalization.md#nls) pro vrácení tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="a8195-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="a8195-117">Další informace o dostupných přepínačích naleznete v článku [globalizace a ICU v .NET](/dotnet/standard/globalization-localization/globalization-icu) .</span><span class="sxs-lookup"><span data-stu-id="a8195-117">For more information about the available switches, see the [.NET globalization and ICU](/dotnet/standard/globalization-localization/globalization-icu) article.</span></span>

#### <a name="category"></a><span data-ttu-id="a8195-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a8195-118">Category</span></span>

<span data-ttu-id="a8195-119">Globalizace</span><span class="sxs-lookup"><span data-stu-id="a8195-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8195-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a8195-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="a8195-121">Většina typů v <xref:System.Globalization?displayProperty=fullName> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="a8195-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
