---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804493"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="173d2-101">IL ret není povoleno v oblasti try</span><span class="sxs-lookup"><span data-stu-id="173d2-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="173d2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="173d2-102">Details</span></span>|<span data-ttu-id="173d2-103">Na rozdíl od kompilátoru just-in-time JIT64 RyuJIT (používaný v rozhraní .NET Framework 4.6) neumožňuje instrukce IL ret v oblasti try.</span><span class="sxs-lookup"><span data-stu-id="173d2-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="173d2-104">Vrácení z oblasti try je zakázáno specifikací ECMA-335 a žádný známý spravovaný kompilátor negeneruje takové IL.</span><span class="sxs-lookup"><span data-stu-id="173d2-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="173d2-105">Kompilátor JIT64 však provede takové IL, pokud je generován pomocí odrazem emit.</span><span class="sxs-lookup"><span data-stu-id="173d2-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="173d2-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="173d2-106">Suggestion</span></span>|<span data-ttu-id="173d2-107">Pokud aplikace generuje IL, který obsahuje ret opcode v oblasti try, aplikace může cílit .NET Framework 4.5 použít staré JIT a vyhnout se této přestávce.</span><span class="sxs-lookup"><span data-stu-id="173d2-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="173d2-108">Alternativně generované IL může být aktualizován vrátit po try oblasti.</span><span class="sxs-lookup"><span data-stu-id="173d2-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="173d2-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="173d2-109">Scope</span></span>|<span data-ttu-id="173d2-110">Edge</span><span class="sxs-lookup"><span data-stu-id="173d2-110">Edge</span></span>|
|<span data-ttu-id="173d2-111">Version</span><span class="sxs-lookup"><span data-stu-id="173d2-111">Version</span></span>|<span data-ttu-id="173d2-112">4.6</span><span class="sxs-lookup"><span data-stu-id="173d2-112">4.6</span></span>|
|<span data-ttu-id="173d2-113">Typ</span><span class="sxs-lookup"><span data-stu-id="173d2-113">Type</span></span>|<span data-ttu-id="173d2-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="173d2-114">Retargeting</span></span>|
