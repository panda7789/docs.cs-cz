---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802692"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="5c120-101">Vylepšení políčku mřížky řádků hvězdičku přidělování algoritmus</span><span class="sxs-lookup"><span data-stu-id="5c120-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5c120-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5c120-102">Details</span></span>|<span data-ttu-id="5c120-103">Oprava chyby v [algoritmus pro přidělování velikostí, které ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) v <xref:System.Windows.Controls.Grid> zavedena v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="5c120-103">Fixed a bug in the [algorithm for allocating sizes to ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="5c120-104">V některých případech, jako je například mřížka s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky uspořádaly nesprávné pozici pravděpodobně mimo mřížky úplně se vynechá.</span><span class="sxs-lookup"><span data-stu-id="5c120-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="5c120-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="5c120-105">Suggestion</span></span>|<span data-ttu-id="5c120-106">Aby aplikace využívat tyto změny musí běžet na 4.8 rozhraní .NET Framework nebo novější.</span><span class="sxs-lookup"><span data-stu-id="5c120-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="5c120-107">Scope</span><span class="sxs-lookup"><span data-stu-id="5c120-107">Scope</span></span>|<span data-ttu-id="5c120-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="5c120-108">Major</span></span>|
|<span data-ttu-id="5c120-109">Version</span><span class="sxs-lookup"><span data-stu-id="5c120-109">Version</span></span>|<span data-ttu-id="5c120-110">4.8</span><span class="sxs-lookup"><span data-stu-id="5c120-110">4.8</span></span>|
|<span data-ttu-id="5c120-111">type</span><span class="sxs-lookup"><span data-stu-id="5c120-111">Type</span></span>|<span data-ttu-id="5c120-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5c120-112">Runtime</span></span>|

