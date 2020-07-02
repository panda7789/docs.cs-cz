---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619917"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="8552d-101">Items. Clear neodebere duplicity z SelectedItems.</span><span class="sxs-lookup"><span data-stu-id="8552d-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="8552d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8552d-102">Details</span></span>

<span data-ttu-id="8552d-103">Předpokládejme, že selektor (s povoleným více výběry) má duplicity v <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> kolekci – stejná položka se vyskytuje více než jednou.</span><span class="sxs-lookup"><span data-stu-id="8552d-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="8552d-104">Odebrání těchto položek ze zdroje dat (např. volání Items. Clear) se neodstraní z; odebere <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> se pouze první instance.</span><span class="sxs-lookup"><span data-stu-id="8552d-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="8552d-105">Kromě toho může následující použití <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (například SelectedItems. Clear ()) narazit na problémy jako <xref:System.ArgumentException?displayProperty=fullName> , protože <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> obsahuje položky, které již nejsou ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8552d-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8552d-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="8552d-106">Suggestion</span></span>

<span data-ttu-id="8552d-107">Upgradujte, pokud je to možné, .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="8552d-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="8552d-108">Name</span><span class="sxs-lookup"><span data-stu-id="8552d-108">Name</span></span>    | <span data-ttu-id="8552d-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8552d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8552d-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8552d-110">Scope</span></span>   |<span data-ttu-id="8552d-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="8552d-111">Minor</span></span>|
|<span data-ttu-id="8552d-112">Verze</span><span class="sxs-lookup"><span data-stu-id="8552d-112">Version</span></span>|<span data-ttu-id="8552d-113">4.5</span><span class="sxs-lookup"><span data-stu-id="8552d-113">4.5</span></span>|
|<span data-ttu-id="8552d-114">Typ</span><span class="sxs-lookup"><span data-stu-id="8552d-114">Type</span></span>|<span data-ttu-id="8552d-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8552d-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8552d-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8552d-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
