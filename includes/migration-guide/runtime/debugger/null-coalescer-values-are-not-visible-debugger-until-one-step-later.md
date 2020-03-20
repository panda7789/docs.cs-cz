---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858841"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="62a31-101">Hodnoty null coalescer nejsou viditelné v ladicím programu až o krok později</span><span class="sxs-lookup"><span data-stu-id="62a31-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="62a31-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="62a31-102">Details</span></span>|<span data-ttu-id="62a31-103">Chyba v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené prostřednictvím operace null coalescing nebudou viditelné v ladicím programu ihned po spuštění operace přiřazení při spuštění v 64bitové verzi rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="62a31-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="62a31-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="62a31-104">Suggestion</span></span>|<span data-ttu-id="62a31-105">Krokování jeden další čas v ladicím programu způsobí, že hodnota místní/pole správně aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="62a31-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="62a31-106">Tento problém byl také vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by měl problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="62a31-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="62a31-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="62a31-107">Scope</span></span>|<span data-ttu-id="62a31-108">Edge</span><span class="sxs-lookup"><span data-stu-id="62a31-108">Edge</span></span>|
|<span data-ttu-id="62a31-109">Version</span><span class="sxs-lookup"><span data-stu-id="62a31-109">Version</span></span>|<span data-ttu-id="62a31-110">4.5</span><span class="sxs-lookup"><span data-stu-id="62a31-110">4.5</span></span>|
|<span data-ttu-id="62a31-111">Typ</span><span class="sxs-lookup"><span data-stu-id="62a31-111">Type</span></span>|<span data-ttu-id="62a31-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="62a31-112">Runtime</span></span>|
