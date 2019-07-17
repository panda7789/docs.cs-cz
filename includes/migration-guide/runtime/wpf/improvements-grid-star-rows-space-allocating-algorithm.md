---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237621"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="5716c-101">Vylepšení políčku mřížky řádků hvězdičku přidělování algoritmus</span><span class="sxs-lookup"><span data-stu-id="5716c-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5716c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5716c-102">Details</span></span>|<span data-ttu-id="5716c-103">Oprava chyby v [algoritmus pro přidělování velikostí, které](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) v <xref:System.Windows.Controls.Grid> zavedena v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="5716c-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="5716c-104">V některých případech, jako je například mřížka s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky uspořádaly nesprávné pozici pravděpodobně mimo mřížky úplně se vynechá.</span><span class="sxs-lookup"><span data-stu-id="5716c-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="5716c-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="5716c-105">Suggestion</span></span>|<span data-ttu-id="5716c-106">Aby aplikace využívat tyto změny musí běžet na 4.8 rozhraní .NET Framework nebo novější.</span><span class="sxs-lookup"><span data-stu-id="5716c-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="5716c-107">Scope</span><span class="sxs-lookup"><span data-stu-id="5716c-107">Scope</span></span>|<span data-ttu-id="5716c-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="5716c-108">Major</span></span>|
|<span data-ttu-id="5716c-109">Version</span><span class="sxs-lookup"><span data-stu-id="5716c-109">Version</span></span>|<span data-ttu-id="5716c-110">4.8</span><span class="sxs-lookup"><span data-stu-id="5716c-110">4.8</span></span>|
|<span data-ttu-id="5716c-111">type</span><span class="sxs-lookup"><span data-stu-id="5716c-111">Type</span></span>|<span data-ttu-id="5716c-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5716c-112">Runtime</span></span>|
