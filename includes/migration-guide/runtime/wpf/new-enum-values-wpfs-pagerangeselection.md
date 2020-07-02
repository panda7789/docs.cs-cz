---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620094"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="880b3-101">Nové hodnoty výčtu v PageRangeSelection WPF</span><span class="sxs-lookup"><span data-stu-id="880b3-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="880b3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="880b3-102">Details</span></span>

<span data-ttu-id="880b3-103">Do výčtu byly přidány dva nové členy ( <xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> a <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName> ) <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="880b3-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="880b3-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="880b3-104">Suggestion</span></span>

<span data-ttu-id="880b3-105">Ve většině případů tyto změny nebudou mít vliv na uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="880b3-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="880b3-106">Kód, který závisí na konkrétním počtu prvků existujících v <xref:System.Enum.GetNames(System.Type)> nebo <xref:System.Enum.GetValues(System.Type)> volání <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> typu, by měl být změněn, i když.</span><span class="sxs-lookup"><span data-stu-id="880b3-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="880b3-107">Name</span><span class="sxs-lookup"><span data-stu-id="880b3-107">Name</span></span>    | <span data-ttu-id="880b3-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="880b3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="880b3-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="880b3-109">Scope</span></span>   |<span data-ttu-id="880b3-110">Edge</span><span class="sxs-lookup"><span data-stu-id="880b3-110">Edge</span></span>|
|<span data-ttu-id="880b3-111">Verze</span><span class="sxs-lookup"><span data-stu-id="880b3-111">Version</span></span>|<span data-ttu-id="880b3-112">4.5</span><span class="sxs-lookup"><span data-stu-id="880b3-112">4.5</span></span>|
|<span data-ttu-id="880b3-113">Typ</span><span class="sxs-lookup"><span data-stu-id="880b3-113">Type</span></span>|<span data-ttu-id="880b3-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="880b3-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="880b3-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="880b3-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
