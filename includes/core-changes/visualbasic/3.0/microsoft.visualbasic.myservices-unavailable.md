---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721788"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="303a3-101">Typy v oboru názvů Microsoft. VisualBasic. MyServices nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="303a3-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="303a3-102">Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="303a3-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="303a3-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="303a3-103">Version introduced</span></span>

<span data-ttu-id="303a3-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="303a3-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="303a3-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="303a3-105">Change description</span></span>

<span data-ttu-id="303a3-106">Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3,0 Preview.</span><span class="sxs-lookup"><span data-stu-id="303a3-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="303a3-107">Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="303a3-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="303a3-108">Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="303a3-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="303a3-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="303a3-109">Recommended action</span></span>

<span data-ttu-id="303a3-110">Pokud váš kód závisí na použití typů **Microsoft. VisualBasic. MyServices** a jejich členů, existují odpovídající typy a členy v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="303a3-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="303a3-111">Následuje mapování typů **Microsoft. VisualBasic. MyServices** na odpovídající typy knihoven tříd .NET:</span><span class="sxs-lookup"><span data-stu-id="303a3-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="303a3-112">Microsoft. VisualBasic. MyServices – typ</span><span class="sxs-lookup"><span data-stu-id="303a3-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="303a3-113">Typ knihovny tříd .NET</span><span class="sxs-lookup"><span data-stu-id="303a3-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="303a3-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>pro aplikace WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> pro model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="303a3-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="303a3-115">Typy v <xref:System.IO> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="303a3-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="303a3-116">Typy související s registrem v <xref:Microsoft.Win32> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="303a3-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="303a3-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="303a3-117">Category</span></span>

<span data-ttu-id="303a3-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="303a3-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="303a3-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="303a3-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
