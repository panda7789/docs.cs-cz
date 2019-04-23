---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803688"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="29f24-101">Volání z obslužné rutiny CellEditEnding DataGrid.CommitEdit zahodí fokus</span><span class="sxs-lookup"><span data-stu-id="29f24-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="29f24-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="29f24-102">Details</span></span>|<span data-ttu-id="29f24-103">Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho z <xref:System.Windows.Controls.DataGrid?displayProperty=name>společnosti <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> způsobí, že obslužné rutiny událostí <xref:System.Windows.Controls.DataGrid?displayProperty=name> ztratí fokus.</span><span class="sxs-lookup"><span data-stu-id="29f24-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="29f24-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="29f24-104">Suggestion</span></span>|<span data-ttu-id="29f24-105">Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže lze se vyhnout upgradem rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29f24-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="29f24-106">Alternativně můžete se vyhnout výběrem explicitně znovu <xref:System.Windows.Controls.DataGrid?displayProperty=name> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="29f24-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="29f24-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="29f24-107">Scope</span></span>|<span data-ttu-id="29f24-108">Edge</span><span class="sxs-lookup"><span data-stu-id="29f24-108">Edge</span></span>|
|<span data-ttu-id="29f24-109">Version</span><span class="sxs-lookup"><span data-stu-id="29f24-109">Version</span></span>|<span data-ttu-id="29f24-110">4.5</span><span class="sxs-lookup"><span data-stu-id="29f24-110">4.5</span></span>|
|<span data-ttu-id="29f24-111">Type</span><span class="sxs-lookup"><span data-stu-id="29f24-111">Type</span></span>|<span data-ttu-id="29f24-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="29f24-112">Runtime</span></span>|
|<span data-ttu-id="29f24-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="29f24-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
