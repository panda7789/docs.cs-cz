---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858841"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="cf036-101">Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později</span><span class="sxs-lookup"><span data-stu-id="cf036-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cf036-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cf036-102">Details</span></span>|<span data-ttu-id="cf036-103">Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené přes operaci sloučení null nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení je spuštěná v 64bitové verzi rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="cf036-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="cf036-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="cf036-104">Suggestion</span></span>|<span data-ttu-id="cf036-105">Krokování další jednou v ladicím programu způsobí, že místní/hodnoty tohoto pole správně aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="cf036-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="cf036-106">Navíc tento problém byl vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by mělo vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="cf036-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="cf036-107">Scope</span><span class="sxs-lookup"><span data-stu-id="cf036-107">Scope</span></span>|<span data-ttu-id="cf036-108">Edge</span><span class="sxs-lookup"><span data-stu-id="cf036-108">Edge</span></span>|
|<span data-ttu-id="cf036-109">Version</span><span class="sxs-lookup"><span data-stu-id="cf036-109">Version</span></span>|<span data-ttu-id="cf036-110">4.5</span><span class="sxs-lookup"><span data-stu-id="cf036-110">4.5</span></span>|
|<span data-ttu-id="cf036-111">type</span><span class="sxs-lookup"><span data-stu-id="cf036-111">Type</span></span>|<span data-ttu-id="cf036-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="cf036-112">Runtime</span></span>|

