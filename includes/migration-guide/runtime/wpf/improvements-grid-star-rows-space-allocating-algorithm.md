---
ms.openlocfilehash: bd3b1cc6a98f01d8c40b4cd67002e79a2c4fe714
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982238"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="8c66c-101">Vylepšení políčku mřížky řádků hvězdičku přidělování algoritmus</span><span class="sxs-lookup"><span data-stu-id="8c66c-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8c66c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8c66c-102">Details</span></span>|<span data-ttu-id="8c66c-103">Oprava chyby v [algoritmus pro přidělování velikostí, které \*-řádků](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) v <xref:System.Windows.Controls.Grid> zavedena v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="8c66c-103">Fixed a bug in the [algorithm for allocating sizes to \*-rows](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="8c66c-104">V některých případech, jako je například mřížka s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky uspořádaly nesprávné pozici pravděpodobně mimo mřížky úplně se vynechá.</span><span class="sxs-lookup"><span data-stu-id="8c66c-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="8c66c-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="8c66c-105">Suggestion</span></span>|<span data-ttu-id="8c66c-106">Aby aplikace využívat tyto změny musí běžet na 4.8 rozhraní .NET Framework nebo novější.</span><span class="sxs-lookup"><span data-stu-id="8c66c-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="8c66c-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8c66c-107">Scope</span></span>|<span data-ttu-id="8c66c-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="8c66c-108">Major</span></span>|
|<span data-ttu-id="8c66c-109">Version</span><span class="sxs-lookup"><span data-stu-id="8c66c-109">Version</span></span>|<span data-ttu-id="8c66c-110">4.8</span><span class="sxs-lookup"><span data-stu-id="8c66c-110">4.8</span></span>|
|<span data-ttu-id="8c66c-111">Type</span><span class="sxs-lookup"><span data-stu-id="8c66c-111">Type</span></span>|<span data-ttu-id="8c66c-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="8c66c-112">Runtime</span></span>|
