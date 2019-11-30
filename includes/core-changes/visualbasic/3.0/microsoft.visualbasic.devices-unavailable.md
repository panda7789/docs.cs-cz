---
ms.openlocfilehash: 4c47b95e98aca727d9f0eda54a167a71fd53afb9
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567450"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="647bc-101">Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="647bc-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="647bc-102">Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="647bc-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="647bc-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="647bc-103">Version introduced</span></span>

<span data-ttu-id="647bc-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="647bc-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="647bc-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="647bc-105">Change description</span></span>

<span data-ttu-id="647bc-106">Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> byly k dispozici v některých verzích .NET Core 3,0 Preview,.</span><span class="sxs-lookup"><span data-stu-id="647bc-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="647bc-107">Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="647bc-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="647bc-108">Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="647bc-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="647bc-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="647bc-109">Recommended action</span></span>

<span data-ttu-id="647bc-110">Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> typy a jejich členů, můžete použít odpovídající typ nebo člen v knihovně třídy .NET.</span><span class="sxs-lookup"><span data-stu-id="647bc-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="647bc-111">Například ekvivalentní funkce pro třídu <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> poskytují typy <xref:System.DateTime?displayProperty=nameWithType> a <xref:System.Environment?displayProperty=nameWithType> a ekvivalentní funkce pro <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> třídy jsou poskytovány typy v oboru názvů <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="647bc-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="647bc-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="647bc-112">Category</span></span>

<span data-ttu-id="647bc-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="647bc-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="647bc-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="647bc-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

