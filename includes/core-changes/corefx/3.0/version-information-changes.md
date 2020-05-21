---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721647"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="87cd3-101">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="87cd3-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="87cd3-102">Mnoho rozhraní API, které vrací verze v rozhraní .NET Core, nyní vrátí verzi produktu místo verze souboru.</span><span class="sxs-lookup"><span data-stu-id="87cd3-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="87cd3-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="87cd3-103">Change description</span></span>

<span data-ttu-id="87cd3-104">V .NET Core 2,2 a předchozích verzích metody jako <xref:System.Environment.Version?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> a dialog vlastností souboru pro sestavení .NET Core odrážejí verzi souboru.</span><span class="sxs-lookup"><span data-stu-id="87cd3-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="87cd3-105">Počínaje .NET Core 3,0 se odrážejí verze produktu.</span><span class="sxs-lookup"><span data-stu-id="87cd3-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="87cd3-106">Následující obrázek znázorňuje rozdíl v informacích o verzi pro sestavení *System. Runtime. dll* pro .net Core 2,2 (vlevo) a .net Core 3,0 (na pravé straně), jak je zobrazeno v dialogovém okně Vlastnosti souboru v **Průzkumníkovi Windows** .</span><span class="sxs-lookup"><span data-stu-id="87cd3-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Rozdíl v informacích o verzi produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="87cd3-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="87cd3-108">Version introduced</span></span>

<span data-ttu-id="87cd3-109">3.0</span><span class="sxs-lookup"><span data-stu-id="87cd3-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87cd3-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="87cd3-110">Recommended action</span></span>

<span data-ttu-id="87cd3-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="87cd3-111">None.</span></span> <span data-ttu-id="87cd3-112">Tato změna by měla v případě, že by byla detekce verze intuitivní, spíše než obtuse.</span><span class="sxs-lookup"><span data-stu-id="87cd3-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="87cd3-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="87cd3-113">Category</span></span>

<span data-ttu-id="87cd3-114">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="87cd3-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87cd3-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="87cd3-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
