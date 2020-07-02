---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621997"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="68033-101">Vylepšení algoritmu přidělujícího místo řádků v mřížce</span><span class="sxs-lookup"><span data-stu-id="68033-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="68033-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="68033-102">Details</span></span>

<span data-ttu-id="68033-103">Opravili jsme chybu v [algoritmu pro přidělování velikostí do](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) v <xref:System.Windows.Controls.Grid> zavedeném v .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="68033-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="68033-104">V některých případech, například v mřížce <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, byly řádky uspořádány na nesprávnou pozici, případně mimo mřížku.</span><span class="sxs-lookup"><span data-stu-id="68033-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="68033-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="68033-105">Suggestion</span></span>

<span data-ttu-id="68033-106">Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4,8 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="68033-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="68033-107">Name</span><span class="sxs-lookup"><span data-stu-id="68033-107">Name</span></span>    | <span data-ttu-id="68033-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="68033-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="68033-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="68033-109">Scope</span></span>   |<span data-ttu-id="68033-110">Hlavní</span><span class="sxs-lookup"><span data-stu-id="68033-110">Major</span></span>|
|<span data-ttu-id="68033-111">Verze</span><span class="sxs-lookup"><span data-stu-id="68033-111">Version</span></span>|<span data-ttu-id="68033-112">4,8</span><span class="sxs-lookup"><span data-stu-id="68033-112">4.8</span></span>|
|<span data-ttu-id="68033-113">Typ</span><span class="sxs-lookup"><span data-stu-id="68033-113">Type</span></span>|<span data-ttu-id="68033-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="68033-114">Runtime</span></span>|
