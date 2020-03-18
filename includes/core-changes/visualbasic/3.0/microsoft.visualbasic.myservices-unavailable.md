---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116362"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="5d99e-101">Typy v oboru názvů Microsoft.VisualBasic.MyServices nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d99e-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="5d99e-102">Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d99e-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5d99e-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="5d99e-103">Version introduced</span></span>

<span data-ttu-id="5d99e-104">.NET Core 3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="5d99e-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="5d99e-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5d99e-105">Change description</span></span>

<span data-ttu-id="5d99e-106">Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3.0 Preview.</span><span class="sxs-lookup"><span data-stu-id="5d99e-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="5d99e-107">Již nejsou k dispozici počínaje rozhraním .NET Core 3.0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="5d99e-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="5d99e-108">Typy byly odebrány, aby se zabránilo zbytečné závislosti sestavení nebo přerušení změny v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="5d99e-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5d99e-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5d99e-109">Recommended action</span></span>

<span data-ttu-id="5d99e-110">Pokud váš kód závisí na použití **Microsoft.VisualBasic.MyServices** typy a jejich členy, existují odpovídající typy a členy v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="5d99e-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="5d99e-111">Následuje mapování typů **Microsoft.VisualBasic.MyServices** na jejich ekvivalentní typy knihovny tříd .NET:</span><span class="sxs-lookup"><span data-stu-id="5d99e-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="5d99e-112">Typ Microsoft.VisualBasic.MyServices</span><span class="sxs-lookup"><span data-stu-id="5d99e-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="5d99e-113">Typ knihovny tříd .NET</span><span class="sxs-lookup"><span data-stu-id="5d99e-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="5d99e-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>pro aplikace WPF pro <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> aplikace windows forms</span><span class="sxs-lookup"><span data-stu-id="5d99e-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="5d99e-115">Typy v <xref:System.IO> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="5d99e-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="5d99e-116">Typy související s <xref:Microsoft.Win32> registrem v oboru názvů</span><span class="sxs-lookup"><span data-stu-id="5d99e-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="5d99e-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5d99e-117">Category</span></span>

<span data-ttu-id="5d99e-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d99e-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5d99e-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5d99e-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
