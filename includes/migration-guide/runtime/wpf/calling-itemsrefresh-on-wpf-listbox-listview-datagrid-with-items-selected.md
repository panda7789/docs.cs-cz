---
ms.openlocfilehash: 710d1517397f423fa40cc0c4a26c3499aac6179e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620082"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a><span data-ttu-id="0feba-101">Volání položek. aktualizace ovládacího prvku ListBox, ListView nebo DataGrid se zvolenými položkami může způsobit, že se v elementu objeví duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="0feba-101">Calling Items.Refresh on a WPF ListBox, ListView, or DataGrid with items selected can cause duplicate items to appear in the element</span></span>

#### <a name="details"></a><span data-ttu-id="0feba-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0feba-102">Details</span></span>

<span data-ttu-id="0feba-103">V .NET Framework 4,5 se voláním ListBox. Items. Refresh z kódu, když jsou vybrané položky v, <xref:System.Windows.Controls.ListBox?displayProperty=fullName> může způsobit, že vybrané položky budou duplikovány v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0feba-103">In the .NET Framework 4.5, calling ListBox.Items.Refresh from code while items are selected in a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> can cause the selected items to be duplicated in the list.</span></span> <span data-ttu-id="0feba-104">K podobnému problému dochází u <xref:System.Windows.Controls.ListView?displayProperty=fullName> a <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="0feba-104">A similar issue occurs with <xref:System.Windows.Controls.ListView?displayProperty=fullName> and <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span></span> <span data-ttu-id="0feba-105">Toto je opraveno v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="0feba-105">This is fixed in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0feba-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="0feba-106">Suggestion</span></span>

<span data-ttu-id="0feba-107">K tomuto problému může dojít v případě, že jste před <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> voláním vyvolali nevybrané položky a pak je znovu vyberete po dokončení volání.</span><span class="sxs-lookup"><span data-stu-id="0feba-107">This issue may be worked around by programmatically unselecting items before <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> is called and then re-selecting them after the call is completed.</span></span> <span data-ttu-id="0feba-108">Případně byl tento problém opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0feba-108">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="0feba-109">Name</span><span class="sxs-lookup"><span data-stu-id="0feba-109">Name</span></span>    | <span data-ttu-id="0feba-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0feba-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0feba-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0feba-111">Scope</span></span>   |<span data-ttu-id="0feba-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="0feba-112">Minor</span></span>|
|<span data-ttu-id="0feba-113">Verze</span><span class="sxs-lookup"><span data-stu-id="0feba-113">Version</span></span>|<span data-ttu-id="0feba-114">4.5</span><span class="sxs-lookup"><span data-stu-id="0feba-114">4.5</span></span>|
|<span data-ttu-id="0feba-115">Typ</span><span class="sxs-lookup"><span data-stu-id="0feba-115">Type</span></span>|<span data-ttu-id="0feba-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="0feba-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0feba-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0feba-117">Affected APIs</span></span>

-<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
