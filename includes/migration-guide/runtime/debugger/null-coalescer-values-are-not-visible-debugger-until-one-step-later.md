---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235219"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="715f8-101">Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později</span><span class="sxs-lookup"><span data-stu-id="715f8-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="715f8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="715f8-102">Details</span></span>|<span data-ttu-id="715f8-103">Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené přes operaci sloučení null nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení je spuštěná v 64bitové verzi rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="715f8-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="715f8-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="715f8-104">Suggestion</span></span>|<span data-ttu-id="715f8-105">Krokování další jednou v ladicím programu způsobí, že místní/hodnoty tohoto pole správně aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="715f8-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="715f8-106">Navíc tento problém byl vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by mělo vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="715f8-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="715f8-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="715f8-107">Scope</span></span>|<span data-ttu-id="715f8-108">Edge</span><span class="sxs-lookup"><span data-stu-id="715f8-108">Edge</span></span>|
|<span data-ttu-id="715f8-109">Version</span><span class="sxs-lookup"><span data-stu-id="715f8-109">Version</span></span>|<span data-ttu-id="715f8-110">4.5</span><span class="sxs-lookup"><span data-stu-id="715f8-110">4.5</span></span>|
|<span data-ttu-id="715f8-111">Type</span><span class="sxs-lookup"><span data-stu-id="715f8-111">Type</span></span>|<span data-ttu-id="715f8-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="715f8-112">Runtime</span></span>|
