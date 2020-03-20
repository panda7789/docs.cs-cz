---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858533"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="1892d-101">Přístup k vybraným položkám WPF DataGrid z obslužné rutiny události UnloadingRow serveru DataGrid může způsobit výjimku NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="1892d-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1892d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1892d-102">Details</span></span>|<span data-ttu-id="1892d-103">Z důvodu chyby v rozhraní .NET Framework 4.5, obslužné rutiny <xref:System.Windows.Controls.DataGrid> událostí pro události zahrnující odebrání řádku může způsobit vyvolání, <xref:System.NullReferenceException?displayProperty=name> pokud mají přístup <xref:System.Windows.Controls.DataGrid>k 's <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> nebo <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1892d-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="1892d-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="1892d-104">Suggestion</span></span>|<span data-ttu-id="1892d-105">Tento problém byl vyřešen v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1892d-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="1892d-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1892d-106">Scope</span></span>|<span data-ttu-id="1892d-107">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="1892d-107">Minor</span></span>|
|<span data-ttu-id="1892d-108">Version</span><span class="sxs-lookup"><span data-stu-id="1892d-108">Version</span></span>|<span data-ttu-id="1892d-109">4.5</span><span class="sxs-lookup"><span data-stu-id="1892d-109">4.5</span></span>|
|<span data-ttu-id="1892d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="1892d-110">Type</span></span>|<span data-ttu-id="1892d-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1892d-111">Runtime</span></span>|
|<span data-ttu-id="1892d-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1892d-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
