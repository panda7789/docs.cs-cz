---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620008"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="f5905-101">Hodnoty null coalescer nejsou v ladicím programu viditelné, dokud jeden krok později</span><span class="sxs-lookup"><span data-stu-id="f5905-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="f5905-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f5905-102">Details</span></span>

<span data-ttu-id="f5905-103">Chyba v .NET Framework 4,5 způsobí, že hodnoty nastavené prostřednictvím operace sloučení s hodnotou null nejsou viditelné v ladicím programu ihned po provedení operace přiřazení, pokud je spuštěná v 64 bitové verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5905-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f5905-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="f5905-104">Suggestion</span></span>

<span data-ttu-id="f5905-105">Krokování jednoho dalšího času v ladicím programu způsobí, že hodnota místního/pole bude správně aktualizována.</span><span class="sxs-lookup"><span data-stu-id="f5905-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="f5905-106">Tento problém se také vyřešil v .NET Framework 4,6; upgrade na tuto verzi rozhraní by měl vyřešit tento problém.</span><span class="sxs-lookup"><span data-stu-id="f5905-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="f5905-107">Name</span><span class="sxs-lookup"><span data-stu-id="f5905-107">Name</span></span>    | <span data-ttu-id="f5905-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f5905-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f5905-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f5905-109">Scope</span></span>   |<span data-ttu-id="f5905-110">Edge</span><span class="sxs-lookup"><span data-stu-id="f5905-110">Edge</span></span>|
|<span data-ttu-id="f5905-111">Verze</span><span class="sxs-lookup"><span data-stu-id="f5905-111">Version</span></span>|<span data-ttu-id="f5905-112">4.5</span><span class="sxs-lookup"><span data-stu-id="f5905-112">4.5</span></span>|
|<span data-ttu-id="f5905-113">Typ</span><span class="sxs-lookup"><span data-stu-id="f5905-113">Type</span></span>|<span data-ttu-id="f5905-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f5905-114">Runtime</span></span>|
