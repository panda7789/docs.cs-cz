---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621109"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="b8750-101">Změna vlastnosti-Enable nadřazené položky ovládacího prvku TextBlock se projeví u všech podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b8750-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="b8750-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b8750-102">Details</span></span>

<span data-ttu-id="b8750-103">Počínaje .NET Framework 4.6.2 se změna <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> vlastnosti nadřazeného <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ovládacího prvku projeví u všech podřízených ovládacích prvků (jako jsou hypertextové odkazy a tlačítka) <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ovládacího prvku. V .NET Framework 4.6.1 a dřívějších verzích ovládací prvky uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> neodrážely stav <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> vlastnosti <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="b8750-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b8750-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="b8750-104">Suggestion</span></span>

<span data-ttu-id="b8750-105">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8750-105">None.</span></span> <span data-ttu-id="b8750-106">Tato změna odpovídá očekávanému chování ovládacích prvků uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b8750-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="b8750-107">Name</span><span class="sxs-lookup"><span data-stu-id="b8750-107">Name</span></span>    | <span data-ttu-id="b8750-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b8750-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b8750-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b8750-109">Scope</span></span>   |<span data-ttu-id="b8750-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="b8750-110">Minor</span></span>|
|<span data-ttu-id="b8750-111">Verze</span><span class="sxs-lookup"><span data-stu-id="b8750-111">Version</span></span>|<span data-ttu-id="b8750-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="b8750-112">4.6.2</span></span>|
|<span data-ttu-id="b8750-113">Typ</span><span class="sxs-lookup"><span data-stu-id="b8750-113">Type</span></span>|<span data-ttu-id="b8750-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b8750-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b8750-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b8750-115">Affected APIs</span></span>

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
