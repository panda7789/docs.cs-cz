---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237621"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="bbe9f-101">Vylepšení gridových řádků prostoru přidělování algoritmu</span><span class="sxs-lookup"><span data-stu-id="bbe9f-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bbe9f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bbe9f-102">Details</span></span>|<span data-ttu-id="bbe9f-103">Opravena chyba v [algoritmu pro přidělování velikostí](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) <xref:System.Windows.Controls.Grid> v souboru .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="bbe9f-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="bbe9f-104">V některých případech, například Grid s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky byly uspořádány na nesprávné pozici, případně mimo Grid úplně.</span><span class="sxs-lookup"><span data-stu-id="bbe9f-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="bbe9f-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="bbe9f-105">Suggestion</span></span>|<span data-ttu-id="bbe9f-106">Aby aplikace mohla využívat tyto změny, musí být spuštěna v rozhraní .NET Framework 4.8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="bbe9f-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="bbe9f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="bbe9f-107">Scope</span></span>|<span data-ttu-id="bbe9f-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="bbe9f-108">Major</span></span>|
|<span data-ttu-id="bbe9f-109">Version</span><span class="sxs-lookup"><span data-stu-id="bbe9f-109">Version</span></span>|<span data-ttu-id="bbe9f-110">4.8</span><span class="sxs-lookup"><span data-stu-id="bbe9f-110">4.8</span></span>|
|<span data-ttu-id="bbe9f-111">Typ</span><span class="sxs-lookup"><span data-stu-id="bbe9f-111">Type</span></span>|<span data-ttu-id="bbe9f-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="bbe9f-112">Runtime</span></span>|
