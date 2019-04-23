---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981615"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="e7fcd-101">Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později</span><span class="sxs-lookup"><span data-stu-id="e7fcd-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e7fcd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e7fcd-102">Details</span></span>|<span data-ttu-id="e7fcd-103">Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené přes operaci sloučení null nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení je spuštěná v 64bitové verzi rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="e7fcd-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="e7fcd-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e7fcd-104">Suggestion</span></span>|<span data-ttu-id="e7fcd-105">Krokování další jednou v ladicím programu způsobí, že místní/hodnoty tohoto pole správně aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="e7fcd-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="e7fcd-106">Navíc tento problém byl vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by mělo vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="e7fcd-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="e7fcd-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e7fcd-107">Scope</span></span>|<span data-ttu-id="e7fcd-108">Edge</span><span class="sxs-lookup"><span data-stu-id="e7fcd-108">Edge</span></span>|
|<span data-ttu-id="e7fcd-109">Version</span><span class="sxs-lookup"><span data-stu-id="e7fcd-109">Version</span></span>|<span data-ttu-id="e7fcd-110">4.5</span><span class="sxs-lookup"><span data-stu-id="e7fcd-110">4.5</span></span>|
|<span data-ttu-id="e7fcd-111">Type</span><span class="sxs-lookup"><span data-stu-id="e7fcd-111">Type</span></span>|<span data-ttu-id="e7fcd-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e7fcd-112">Runtime</span></span>|
