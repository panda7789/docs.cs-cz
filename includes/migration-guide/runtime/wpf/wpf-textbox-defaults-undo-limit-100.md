---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620102"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="123ad-101">Výchozím textovým polem WPF je omezení vrácení 100</span><span class="sxs-lookup"><span data-stu-id="123ad-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="123ad-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="123ad-102">Details</span></span>

<span data-ttu-id="123ad-103">V .NET Framework 4,5 je výchozí limit vrácení pro textové pole WPF (WPF) 100 (na rozdíl od neomezených .NET Framework 4,0).</span><span class="sxs-lookup"><span data-stu-id="123ad-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="123ad-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="123ad-104">Suggestion</span></span>

<span data-ttu-id="123ad-105">Pokud je limit vrácení 100 příliš nízký, lze limit nastavit explicitně na<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="123ad-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="123ad-106">Name</span><span class="sxs-lookup"><span data-stu-id="123ad-106">Name</span></span>    | <span data-ttu-id="123ad-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="123ad-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="123ad-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="123ad-108">Scope</span></span>   |<span data-ttu-id="123ad-109">Edge</span><span class="sxs-lookup"><span data-stu-id="123ad-109">Edge</span></span>|
|<span data-ttu-id="123ad-110">Verze</span><span class="sxs-lookup"><span data-stu-id="123ad-110">Version</span></span>|<span data-ttu-id="123ad-111">4.5</span><span class="sxs-lookup"><span data-stu-id="123ad-111">4.5</span></span>|
|<span data-ttu-id="123ad-112">Typ</span><span class="sxs-lookup"><span data-stu-id="123ad-112">Type</span></span>|<span data-ttu-id="123ad-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="123ad-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="123ad-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="123ad-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
