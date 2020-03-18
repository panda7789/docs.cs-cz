---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449392"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="e6c1a-101">UnauthorizedAccessException vyvoláno souborem FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="e6c1a-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="e6c1a-102">V .NET Core <xref:System.UnauthorizedAccessException> je vyvolána, když se volající pokusí nastavit hodnotu atributu souboru, ale nemá oprávnění k zápisu.</span><span class="sxs-lookup"><span data-stu-id="e6c1a-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e6c1a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e6c1a-103">Change description</span></span>

<span data-ttu-id="e6c1a-104">V rozhraní .NET <xref:System.ArgumentException> Framework je vyvolána, když se volající <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> pokusí nastavit hodnotu atributu souboru, ale nemá oprávnění k zápisu.</span><span class="sxs-lookup"><span data-stu-id="e6c1a-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="e6c1a-105">V .NET Core <xref:System.UnauthorizedAccessException> je místo toho vyvolána.</span><span class="sxs-lookup"><span data-stu-id="e6c1a-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="e6c1a-106">(V .NET Core, je <xref:System.ArgumentException> stále vyvolána, pokud volající pokusí nastavit atribut neplatný soubor.)</span><span class="sxs-lookup"><span data-stu-id="e6c1a-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e6c1a-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="e6c1a-107">Version introduced</span></span>

<span data-ttu-id="e6c1a-108">1.0</span><span class="sxs-lookup"><span data-stu-id="e6c1a-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e6c1a-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e6c1a-109">Recommended action</span></span>

<span data-ttu-id="e6c1a-110">Upravte `catch` všechny příkazy zachytit <xref:System.UnauthorizedAccessException> místo nebo vedle <xref:System.ArgumentException>, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="e6c1a-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="e6c1a-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e6c1a-111">Category</span></span>

<span data-ttu-id="e6c1a-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e6c1a-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e6c1a-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e6c1a-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
