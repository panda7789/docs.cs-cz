---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937040"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="d03ed-101">Duplicitní api odebraná z formulářů systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d03ed-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="d03ed-102">V rozhraní .NET Core 3.0 RC1 byl odebrán počet rozhraní API, která byla omylem duplikována v oboru <xref:System.Windows.Forms?displayProperty=fullName> názvů počínaje rozhraním .NET Core 3.0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="d03ed-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d03ed-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="d03ed-103">Change description</span></span>

<span data-ttu-id="d03ed-104">.NET Core 3.0 Preview 4 neúmyslně duplikoval počet typů v oboru <xref:System.Windows.Forms?displayProperty=fullName> názvů, které již v oboru <xref:System.ComponentModel.Design?displayProperty=fullName> názvů existovaly.</span><span class="sxs-lookup"><span data-stu-id="d03ed-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="d03ed-105">Počínaje rozhraním .NET Core 3.0 RC1 již tyto duplicitní typy nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d03ed-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="d03ed-106">V následující tabulce je uveden původní typ a jeho duplicitní typ:</span><span class="sxs-lookup"><span data-stu-id="d03ed-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="d03ed-107">Původní typ</span><span class="sxs-lookup"><span data-stu-id="d03ed-107">Original type</span></span>|<span data-ttu-id="d03ed-108">Duplicitní typ</span><span class="sxs-lookup"><span data-stu-id="d03ed-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="d03ed-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="d03ed-109">Version introduced</span></span>

<span data-ttu-id="d03ed-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="d03ed-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d03ed-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d03ed-111">Recommended action</span></span>

<span data-ttu-id="d03ed-112">Aktualizujte kód tak, aby odkazoval na původní typ, jak je znázorněno ve sloupci **Původní typ** tabulky.</span><span class="sxs-lookup"><span data-stu-id="d03ed-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="d03ed-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d03ed-113">Category</span></span>

<span data-ttu-id="d03ed-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d03ed-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d03ed-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d03ed-115">Affected APIs</span></span>

- <span data-ttu-id="d03ed-116">Nelze zjistit pomocí analýzy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d03ed-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
