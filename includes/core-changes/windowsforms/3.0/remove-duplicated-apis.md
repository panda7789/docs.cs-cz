---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937040"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="b1533-101">Odebrala se duplicitní rozhraní API z model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b1533-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="b1533-102">V .NET Core 3,0 RC1 se odebralo několik rozhraní API náhodně duplicitních z oboru názvů <xref:System.Windows.Forms?displayProperty=fullName> od verze .NET Core 3,0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="b1533-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b1533-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b1533-103">Change description</span></span>

<span data-ttu-id="b1533-104">.NET Core 3,0 Preview 4 neúmyslně duplikoval určitý počet typů v oboru názvů <xref:System.Windows.Forms?displayProperty=fullName>, který již existoval v <xref:System.ComponentModel.Design?displayProperty=fullName>m oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b1533-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="b1533-105">Od verze .NET Core 3,0 RC1 tyto duplicitní typy již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1533-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="b1533-106">V následující tabulce je uveden původní typ a jeho duplicitní typ:</span><span class="sxs-lookup"><span data-stu-id="b1533-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="b1533-107">Původní typ</span><span class="sxs-lookup"><span data-stu-id="b1533-107">Original type</span></span>|<span data-ttu-id="b1533-108">Duplicitní typ</span><span class="sxs-lookup"><span data-stu-id="b1533-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="b1533-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b1533-109">Version introduced</span></span>

<span data-ttu-id="b1533-110">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="b1533-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b1533-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b1533-111">Recommended action</span></span>

<span data-ttu-id="b1533-112">Aktualizujte kód tak, aby odkazoval na původní typ, jak je znázorněno ve sloupci **původní typ** tabulky.</span><span class="sxs-lookup"><span data-stu-id="b1533-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="b1533-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b1533-113">Category</span></span>

<span data-ttu-id="b1533-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1533-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1533-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b1533-115">Affected APIs</span></span>

- <span data-ttu-id="b1533-116">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b1533-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
