---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803205"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="34471-101">Volání DataGrid.CommitEdit z obslužné rutiny CellEditEnding klesne fokus</span><span class="sxs-lookup"><span data-stu-id="34471-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="34471-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="34471-102">Details</span></span>|<span data-ttu-id="34471-103">Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho <xref:System.Windows.Controls.DataGrid?displayProperty=name>z <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> obslužné rutiny události 's způsobí, <xref:System.Windows.Controls.DataGrid?displayProperty=name> že ztratí fokus.</span><span class="sxs-lookup"><span data-stu-id="34471-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="34471-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="34471-104">Suggestion</span></span>|<span data-ttu-id="34471-105">Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže se jí lze vyhnout upgradem rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34471-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="34471-106">Alternativně se lze vyhnout explicitním opětovným <xref:System.Windows.Controls.DataGrid?displayProperty=name> výběrem <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>po volání .</span><span class="sxs-lookup"><span data-stu-id="34471-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="34471-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="34471-107">Scope</span></span>|<span data-ttu-id="34471-108">Edge</span><span class="sxs-lookup"><span data-stu-id="34471-108">Edge</span></span>|
|<span data-ttu-id="34471-109">Version</span><span class="sxs-lookup"><span data-stu-id="34471-109">Version</span></span>|<span data-ttu-id="34471-110">4.5</span><span class="sxs-lookup"><span data-stu-id="34471-110">4.5</span></span>|
|<span data-ttu-id="34471-111">Typ</span><span class="sxs-lookup"><span data-stu-id="34471-111">Type</span></span>|<span data-ttu-id="34471-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="34471-112">Runtime</span></span>|
|<span data-ttu-id="34471-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="34471-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
