---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567422"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="02b69-101">Typy v oboru názvů Microsoft. VisualBasic. MyServices nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="02b69-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="02b69-102">Typy v oboru názvů <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="02b69-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="02b69-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="02b69-103">Version introduced</span></span>

<span data-ttu-id="02b69-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="02b69-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="02b69-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="02b69-105">Change description</span></span>

<span data-ttu-id="02b69-106">Typy v oboru názvů <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> byly k dispozici v některých verzích .NET Core 3,0 Preview.</span><span class="sxs-lookup"><span data-stu-id="02b69-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="02b69-107">Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="02b69-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="02b69-108">Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.</span><span class="sxs-lookup"><span data-stu-id="02b69-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="02b69-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="02b69-109">Recommended action</span></span>

<span data-ttu-id="02b69-110">Pokud váš kód závisí na použití typů **Microsoft. VisualBasic. MyServices** a jejich členů, existují odpovídající typy a členy v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="02b69-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="02b69-111">Následuje mapování typů **Microsoft. VisualBasic. MyServices** na odpovídající typy knihoven tříd .NET:</span><span class="sxs-lookup"><span data-stu-id="02b69-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="02b69-112">Microsoft. VisualBasic. MyServices – typ</span><span class="sxs-lookup"><span data-stu-id="02b69-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="02b69-113">Typ knihovny tříd .NET</span><span class="sxs-lookup"><span data-stu-id="02b69-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="02b69-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> pro aplikace WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> pro model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="02b69-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="02b69-115">Typy v oboru názvů <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="02b69-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="02b69-116">Typy související s registrem v oboru názvů <xref:Microsoft.Win32></span><span class="sxs-lookup"><span data-stu-id="02b69-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="02b69-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="02b69-117">Category</span></span>

<span data-ttu-id="02b69-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02b69-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="02b69-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="02b69-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

