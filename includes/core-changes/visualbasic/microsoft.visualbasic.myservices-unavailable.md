---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181791"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="e3a8f-101">Typy v oboru názvů Microsoft. VisualBasic. MyServices nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e3a8f-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="e3a8f-102">Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e3a8f-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e3a8f-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e3a8f-103">Version introduced</span></span>

<span data-ttu-id="e3a8f-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e3a8f-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="e3a8f-105">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e3a8f-105">Details</span></span>

<span data-ttu-id="e3a8f-106">Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3,0 Preview,.</span><span class="sxs-lookup"><span data-stu-id="e3a8f-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="e3a8f-107">Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e3a8f-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="e3a8f-108">Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="e3a8f-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="e3a8f-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e3a8f-109">Recommended action</span></span>

<span data-ttu-id="e3a8f-110">Pokud váš kód závisí na použití typů **Microsoft. VisualBasic. MyServices** a jejich členů, existují odpovídající typy a členy v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="e3a8f-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="e3a8f-111">Následuje mapování typů **Microsoft. VisualBasic. MyServices** na odpovídající typy knihoven tříd .NET:</span><span class="sxs-lookup"><span data-stu-id="e3a8f-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="e3a8f-112">Microsoft. VisualBasic. MyServices – typ</span><span class="sxs-lookup"><span data-stu-id="e3a8f-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="e3a8f-113">Typ knihovny tříd .NET</span><span class="sxs-lookup"><span data-stu-id="e3a8f-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="e3a8f-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>pro aplikace <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> WPF pro model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="e3a8f-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="e3a8f-115">Typy v <xref:System.IO> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="e3a8f-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="e3a8f-116">Typy související s registrem v <xref:Microsoft.Win32> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="e3a8f-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="e3a8f-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e3a8f-117">Category</span></span>

<span data-ttu-id="e3a8f-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3a8f-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e3a8f-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e3a8f-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

