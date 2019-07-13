---
ms.openlocfilehash: 4b87fb0161059eb9df919a64a9966c00177caf89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858533"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="58462-101">Přístup k WPF DataGrid vybrané položky z obslužné rutiny události UnloadingRow DataGrid může způsobit NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="58462-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="58462-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="58462-102">Details</span></span>|<span data-ttu-id="58462-103">Kvůli chybě v rozhraní .NET Framework 4.5, obslužné rutiny událostí pro <xref:System.Windows.Controls.DataGrid> události týkající se odebrání řádek může způsobit, že <xref:System.NullReferenceException?displayProperty=name> která je vyvolána, pokud budou přistupovat k <xref:System.Windows.Controls.DataGrid>společnosti <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> nebo <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58462-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="58462-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="58462-104">Suggestion</span></span>|<span data-ttu-id="58462-105">Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58462-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="58462-106">Scope</span><span class="sxs-lookup"><span data-stu-id="58462-106">Scope</span></span>|<span data-ttu-id="58462-107">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="58462-107">Minor</span></span>|
|<span data-ttu-id="58462-108">Version</span><span class="sxs-lookup"><span data-stu-id="58462-108">Version</span></span>|<span data-ttu-id="58462-109">4.5</span><span class="sxs-lookup"><span data-stu-id="58462-109">4.5</span></span>|
|<span data-ttu-id="58462-110">type</span><span class="sxs-lookup"><span data-stu-id="58462-110">Type</span></span>|<span data-ttu-id="58462-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="58462-111">Runtime</span></span>|
|<span data-ttu-id="58462-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="58462-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

