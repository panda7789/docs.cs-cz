---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116319"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="16d1e-101">Typy v oboru názvů Microsoft.VisualBasic.Devices nejsou k dispozici</span><span class="sxs-lookup"><span data-stu-id="16d1e-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="16d1e-102">Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="16d1e-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="16d1e-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="16d1e-103">Version introduced</span></span>

<span data-ttu-id="16d1e-104">.NET Core 3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="16d1e-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="16d1e-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="16d1e-105">Change description</span></span>

<span data-ttu-id="16d1e-106">Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3.0 Preview..</span><span class="sxs-lookup"><span data-stu-id="16d1e-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="16d1e-107">Již nejsou k dispozici počínaje rozhraním .NET Core 3.0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="16d1e-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="16d1e-108">Typy byly odebrány, aby se zabránilo zbytečné závislosti sestavení nebo přerušení změny v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="16d1e-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="16d1e-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="16d1e-109">Recommended action</span></span>

<span data-ttu-id="16d1e-110">Pokud váš kód závisí <xref:Microsoft.VisualBasic.Devices> na použití typů a jejich členů, můžete použít odpovídající typ nebo člen v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="16d1e-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="16d1e-111">Například ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> třídy je poskytována <xref:System.DateTime?displayProperty=nameWithType> <xref:System.Environment?displayProperty=nameWithType> a typy a ekvivalentní <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> funkce třídy je poskytována typy v oboru <xref:System.IO.Ports?displayProperty=nameWithType> názvů.</span><span class="sxs-lookup"><span data-stu-id="16d1e-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="16d1e-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="16d1e-112">Category</span></span>

<span data-ttu-id="16d1e-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16d1e-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="16d1e-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="16d1e-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
