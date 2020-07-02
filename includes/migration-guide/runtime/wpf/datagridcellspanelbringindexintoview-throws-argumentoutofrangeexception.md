---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622347"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="f5908-101">DataGridCellsPanel. BringIndexIntoView vyvolá výjimku ArgumentOutOfRangeException.</span><span class="sxs-lookup"><span data-stu-id="f5908-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="f5908-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f5908-102">Details</span></span>

<span data-ttu-id="f5908-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>bude pracovat asynchronně, pokud je povolena virtualizace sloupce, ale ještě nebyly určeny šířky sloupců.</span><span class="sxs-lookup"><span data-stu-id="f5908-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="f5908-104">Pokud jsou sloupce odebrány před tím, než dojde k asynchronní práci, <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> může dojít k chybě.</span><span class="sxs-lookup"><span data-stu-id="f5908-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f5908-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="f5908-105">Suggestion</span></span>

<span data-ttu-id="f5908-106">Jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="f5908-106">Any one of the following:</span></span><ol><li><span data-ttu-id="f5908-107">Upgradujte na .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="f5908-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="f5908-108">Nainstalujte nejnovější servisní opravu pro .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="f5908-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="f5908-109">Vyhněte se odebírání sloupců, dokud nebude <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> dokončena asynchronní odpověď.</span><span class="sxs-lookup"><span data-stu-id="f5908-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="f5908-110">Name</span><span class="sxs-lookup"><span data-stu-id="f5908-110">Name</span></span>    | <span data-ttu-id="f5908-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f5908-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f5908-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f5908-112">Scope</span></span>   |<span data-ttu-id="f5908-113">Edge</span><span class="sxs-lookup"><span data-stu-id="f5908-113">Edge</span></span>|
|<span data-ttu-id="f5908-114">Verze</span><span class="sxs-lookup"><span data-stu-id="f5908-114">Version</span></span>|<span data-ttu-id="f5908-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f5908-115">4.6.2</span></span>|
|<span data-ttu-id="f5908-116">Typ</span><span class="sxs-lookup"><span data-stu-id="f5908-116">Type</span></span>|<span data-ttu-id="f5908-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f5908-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f5908-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f5908-118">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
