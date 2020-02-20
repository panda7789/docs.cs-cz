---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449392"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="e00fd-101">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="e00fd-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="e00fd-102">V rozhraní .NET Core je vyvolána <xref:System.UnauthorizedAccessException>, když se volající pokusí nastavit hodnotu atributu souboru, ale nemá oprávnění k zápisu.</span><span class="sxs-lookup"><span data-stu-id="e00fd-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e00fd-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="e00fd-103">Change description</span></span>

<span data-ttu-id="e00fd-104">V .NET Framework je vyvolána <xref:System.ArgumentException> při pokusu volajícího o nastavení hodnoty atributu souboru v <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, ale nemá oprávnění k zápisu.</span><span class="sxs-lookup"><span data-stu-id="e00fd-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="e00fd-105">V .NET Core je místo toho vyvolána <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="e00fd-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="e00fd-106">(V rozhraní .NET Core je <xref:System.ArgumentException> stále vyvolána, pokud se volající pokusí nastavit neplatný atribut souboru.)</span><span class="sxs-lookup"><span data-stu-id="e00fd-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e00fd-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e00fd-107">Version introduced</span></span>

<span data-ttu-id="e00fd-108">1.0</span><span class="sxs-lookup"><span data-stu-id="e00fd-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e00fd-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e00fd-109">Recommended action</span></span>

<span data-ttu-id="e00fd-110">V případě potřeby upravte jakékoli příkazy `catch` k zachytávání <xref:System.UnauthorizedAccessException> namísto, případně i <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e00fd-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="e00fd-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e00fd-111">Category</span></span>

<span data-ttu-id="e00fd-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e00fd-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e00fd-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e00fd-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
