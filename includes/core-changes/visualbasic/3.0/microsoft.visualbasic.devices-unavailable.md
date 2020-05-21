---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721101"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="8c662-101">Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8c662-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="8c662-102">Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8c662-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c662-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8c662-103">Version introduced</span></span>

<span data-ttu-id="8c662-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="8c662-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="8c662-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8c662-105">Change description</span></span>

<span data-ttu-id="8c662-106">Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3,0 Preview,.</span><span class="sxs-lookup"><span data-stu-id="8c662-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="8c662-107">Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8c662-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="8c662-108">Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="8c662-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c662-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8c662-109">Recommended action</span></span>

<span data-ttu-id="8c662-110">Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> typů a jejich členů, může být možné použít odpovídající typ nebo člen v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="8c662-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="8c662-111">Například ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> třídy jsou poskytovány <xref:System.DateTime?displayProperty=nameWithType> typy a a <xref:System.Environment?displayProperty=nameWithType> ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> třídy jsou poskytovány typy v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8c662-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="8c662-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8c662-112">Category</span></span>

<span data-ttu-id="8c662-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c662-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c662-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8c662-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
