---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622028"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="6c576-101">Volání metody DataGrid. CommitEdit z obslužné rutiny CellEditEnding zruší fokus.</span><span class="sxs-lookup"><span data-stu-id="6c576-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="6c576-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6c576-102">Details</span></span>

<span data-ttu-id="6c576-103">Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jedné z <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> obslužných rutin událostí způsobí <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> ztrátu fokusu.</span><span class="sxs-lookup"><span data-stu-id="6c576-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6c576-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="6c576-104">Suggestion</span></span>

<span data-ttu-id="6c576-105">Tato chyba byla opravena v .NET Framework 4.5.2, takže se ji můžete vyhnout upgradem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c576-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="6c576-106">Alternativně se můžete vyhnout explicitním výběrem <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="6c576-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="6c576-107">Name</span><span class="sxs-lookup"><span data-stu-id="6c576-107">Name</span></span>    | <span data-ttu-id="6c576-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6c576-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6c576-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6c576-109">Scope</span></span>   |<span data-ttu-id="6c576-110">Edge</span><span class="sxs-lookup"><span data-stu-id="6c576-110">Edge</span></span>|
|<span data-ttu-id="6c576-111">Verze</span><span class="sxs-lookup"><span data-stu-id="6c576-111">Version</span></span>|<span data-ttu-id="6c576-112">4.5</span><span class="sxs-lookup"><span data-stu-id="6c576-112">4.5</span></span>|
|<span data-ttu-id="6c576-113">Typ</span><span class="sxs-lookup"><span data-stu-id="6c576-113">Type</span></span>|<span data-ttu-id="6c576-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="6c576-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6c576-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6c576-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
