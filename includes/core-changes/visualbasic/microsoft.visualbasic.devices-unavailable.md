---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237324"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="5fc06-101">Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5fc06-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="5fc06-102">Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5fc06-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5fc06-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5fc06-103">Version introduced</span></span>

<span data-ttu-id="5fc06-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="5fc06-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="5fc06-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="5fc06-105">Change description</span></span>

<span data-ttu-id="5fc06-106">Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> byly k dispozici v některých verzích .NET Core 3,0 Preview,.</span><span class="sxs-lookup"><span data-stu-id="5fc06-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="5fc06-107">Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5fc06-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="5fc06-108">Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="5fc06-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="5fc06-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5fc06-109">Recommended action</span></span>

<span data-ttu-id="5fc06-110">Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> a jejich členů, může být možné použít odpovídající typ nebo člen v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="5fc06-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="5fc06-111">Například ekvivalentní funkce pro třídu <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> je poskytována typy <xref:System.DateTime?displayProperty=nameWithType> a <xref:System.Environment?displayProperty=nameWithType> a ekvivalentní funkce třídy <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> jsou poskytovány typy v oboru názvů <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fc06-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="5fc06-112">Category</span><span class="sxs-lookup"><span data-stu-id="5fc06-112">Category</span></span>

<span data-ttu-id="5fc06-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fc06-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5fc06-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5fc06-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

