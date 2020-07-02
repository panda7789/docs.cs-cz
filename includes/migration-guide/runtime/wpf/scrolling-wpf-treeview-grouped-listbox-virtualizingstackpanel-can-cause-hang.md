---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622053"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="0c5a5-101">Posouvání zobrazení stromu WPF nebo seskupeného seznamu ve VirtualizingStackPanel může způsobit zablokování</span><span class="sxs-lookup"><span data-stu-id="0c5a5-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="0c5a5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0c5a5-102">Details</span></span>

<span data-ttu-id="0c5a5-103">V .NET Framework v 4.5 může posouvání WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> na virtualizovaném panelu zásobníku způsobit zablokování, pokud jsou v zobrazení okraje (například mezi položkami v <xref:System.Windows.Controls.TreeView?displayProperty=fullName> , například nebo na prvku ItemsPresenter).</span><span class="sxs-lookup"><span data-stu-id="0c5a5-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="0c5a5-104">V některých případech mohou různé velikosti položek v zobrazení způsobit nestabilitu i v případě, že nejsou k dispozici žádné okraje.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0c5a5-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="0c5a5-105">Suggestion</span></span>

<span data-ttu-id="0c5a5-106">Tato chyba se může vyhnout upgradem na .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="0c5a5-107">Alternativně lze marže odebrat z kolekce zobrazení (například <xref:System.Windows.Controls.TreeView?displayProperty=fullName> s) v rámci virtualizovaných panelů zásobníku, pokud všechny obsažené položky mají stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="0c5a5-108">Name</span><span class="sxs-lookup"><span data-stu-id="0c5a5-108">Name</span></span>    | <span data-ttu-id="0c5a5-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0c5a5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0c5a5-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0c5a5-110">Scope</span></span>   |<span data-ttu-id="0c5a5-111">Hlavní</span><span class="sxs-lookup"><span data-stu-id="0c5a5-111">Major</span></span>|
|<span data-ttu-id="0c5a5-112">Verze</span><span class="sxs-lookup"><span data-stu-id="0c5a5-112">Version</span></span>|<span data-ttu-id="0c5a5-113">4.5</span><span class="sxs-lookup"><span data-stu-id="0c5a5-113">4.5</span></span>|
|<span data-ttu-id="0c5a5-114">Typ</span><span class="sxs-lookup"><span data-stu-id="0c5a5-114">Type</span></span>|<span data-ttu-id="0c5a5-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="0c5a5-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c5a5-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0c5a5-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
