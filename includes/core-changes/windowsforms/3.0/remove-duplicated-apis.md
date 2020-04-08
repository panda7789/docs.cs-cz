---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888109"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="c5f42-101">Duplicitní api odebraná z formulářů systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5f42-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="c5f42-102">V rozhraní .NET Core 3.0 RC1 byl odebrán počet rozhraní API, která byla omylem duplikována v oboru <xref:System.Windows.Forms?displayProperty=fullName> názvů počínaje rozhraním .NET Core 3.0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="c5f42-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c5f42-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="c5f42-103">Change description</span></span>

<span data-ttu-id="c5f42-104">.NET Core 3.0 Preview 4 neúmyslně duplikoval počet typů v oboru <xref:System.Windows.Forms?displayProperty=fullName> názvů, které již v oboru <xref:System.ComponentModel.Design?displayProperty=fullName> názvů existovaly.</span><span class="sxs-lookup"><span data-stu-id="c5f42-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="c5f42-105">Počínaje rozhraním .NET Core 3.0 RC1 již tyto duplicitní typy nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c5f42-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="c5f42-106">V následující tabulce je uveden původní typ a jeho duplicitní typ:</span><span class="sxs-lookup"><span data-stu-id="c5f42-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="c5f42-107">Původní typ</span><span class="sxs-lookup"><span data-stu-id="c5f42-107">Original type</span></span>|<span data-ttu-id="c5f42-108">Duplicitní typ</span><span class="sxs-lookup"><span data-stu-id="c5f42-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="c5f42-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="c5f42-109">Version introduced</span></span>

<span data-ttu-id="c5f42-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="c5f42-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5f42-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c5f42-111">Recommended action</span></span>

<span data-ttu-id="c5f42-112">Aktualizujte kód tak, aby odkazoval na původní typ, jak je znázorněno ve sloupci **Původní typ** tabulky.</span><span class="sxs-lookup"><span data-stu-id="c5f42-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="c5f42-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c5f42-113">Category</span></span>

<span data-ttu-id="c5f42-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5f42-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5f42-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c5f42-115">Affected APIs</span></span>

- <span data-ttu-id="c5f42-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="c5f42-116">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
