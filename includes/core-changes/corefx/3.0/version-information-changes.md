---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344462"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="781fa-101">Api, která sestavy verze nyní sestavy produktu a není verze souboru</span><span class="sxs-lookup"><span data-stu-id="781fa-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="781fa-102">Mnoho rozhraní API, která vracejí verze v rozhraní .NET Core, nyní vrací verzi produktu, nikoli verzi souboru.</span><span class="sxs-lookup"><span data-stu-id="781fa-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="781fa-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="781fa-103">Change description</span></span>

<span data-ttu-id="781fa-104">V rozhraní .NET Core 2.2 a <xref:System.Environment.Version?displayProperty=nameWithType>předchozích verzích odrážejí verze souboru metody jako , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>a dialogové okno vlastností souboru pro sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="781fa-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="781fa-105">Počínaje rozhraním .NET Core 3.0 odrážejí verzi produktu.</span><span class="sxs-lookup"><span data-stu-id="781fa-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="781fa-106">Následující obrázek znázorňuje rozdíl v informacích o verzi pro sestavení *System.Runtime.dll* pro rozhraní .NET Core 2.2 (vlevo) a .NET Core 3.0 (vpravo), jak je zobrazeno v dialogovém okně vlastností souboru **průzkumníka Windows.**</span><span class="sxs-lookup"><span data-stu-id="781fa-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Rozdíl v informacích o verzi produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="781fa-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="781fa-108">Version introduced</span></span>

<span data-ttu-id="781fa-109">3.0</span><span class="sxs-lookup"><span data-stu-id="781fa-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="781fa-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="781fa-110">Recommended action</span></span>

<span data-ttu-id="781fa-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="781fa-111">None.</span></span> <span data-ttu-id="781fa-112">Tato změna by měla provést detekci verze intuitivní spíše než tupý.</span><span class="sxs-lookup"><span data-stu-id="781fa-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="781fa-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="781fa-113">Category</span></span>

<span data-ttu-id="781fa-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="781fa-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="781fa-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="781fa-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
