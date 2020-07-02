---
ms.openlocfilehash: 7ac0cac53ab2fa7657d0ae58f11d9e777631acc9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620089"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="2437e-101">Přístup k vybraným položkám ovládacího prvku DataGrid v GRAFICKÉm přístupu z obslužné rutiny události UnloadingRow objektu DataGrid může způsobit NullReferenceException.</span><span class="sxs-lookup"><span data-stu-id="2437e-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="2437e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2437e-102">Details</span></span>

<span data-ttu-id="2437e-103">V důsledku chyby v .NET Framework 4,5 může obslužná rutina události pro <xref:System.Windows.Controls.DataGrid> události zahrnující odebrání řádku způsobit <xref:System.NullReferenceException?displayProperty=fullName> vyvolání, pokud přistupuje k <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> vlastnostem nebo.</span><span class="sxs-lookup"><span data-stu-id="2437e-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2437e-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="2437e-104">Suggestion</span></span>

<span data-ttu-id="2437e-105">Tento problém byl opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2437e-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="2437e-106">Name</span><span class="sxs-lookup"><span data-stu-id="2437e-106">Name</span></span>    | <span data-ttu-id="2437e-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2437e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2437e-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2437e-108">Scope</span></span>   |<span data-ttu-id="2437e-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="2437e-109">Minor</span></span>|
|<span data-ttu-id="2437e-110">Verze</span><span class="sxs-lookup"><span data-stu-id="2437e-110">Version</span></span>|<span data-ttu-id="2437e-111">4.5</span><span class="sxs-lookup"><span data-stu-id="2437e-111">4.5</span></span>|
|<span data-ttu-id="2437e-112">Typ</span><span class="sxs-lookup"><span data-stu-id="2437e-112">Type</span></span>|<span data-ttu-id="2437e-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2437e-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2437e-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2437e-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
