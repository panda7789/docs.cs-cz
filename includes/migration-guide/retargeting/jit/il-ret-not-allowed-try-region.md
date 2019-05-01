---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088458"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="74b6f-101">IL není povolena v oblasti, zkuste vrácená hodnota:</span><span class="sxs-lookup"><span data-stu-id="74b6f-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="74b6f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="74b6f-102">Details</span></span>|<span data-ttu-id="74b6f-103">Na rozdíl od kompilátor just-in-time JIT64 komponentách RyuJIT (používá se v rozhraní .NET Framework 4.6) neumožňuje IL staré instrukce v oblasti try.</span><span class="sxs-lookup"><span data-stu-id="74b6f-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="74b6f-104">Návrat z oblasti try se nepovoluje specifikací ECMA-335 a žádné známé spravovaný kompilátor vygeneruje taková IL.</span><span class="sxs-lookup"><span data-stu-id="74b6f-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="74b6f-105">Však kompilátor JIT64 se spustí tyto IL je generována pomocí operace reflection emit.</span><span class="sxs-lookup"><span data-stu-id="74b6f-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="74b6f-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="74b6f-106">Suggestion</span></span>|<span data-ttu-id="74b6f-107">Pokud aplikace generuje IL, který obsahuje operační kód ret v oblasti, zkuste, aplikace mohou být zaměřeny na rozhraní .NET Framework 4.5 používat staré JIT a vyhnout se této přerušení.</span><span class="sxs-lookup"><span data-stu-id="74b6f-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="74b6f-108">Alternativně může být aktualizován IL generovaný vrátit zkuste oblasti.</span><span class="sxs-lookup"><span data-stu-id="74b6f-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="74b6f-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="74b6f-109">Scope</span></span>|<span data-ttu-id="74b6f-110">Edge</span><span class="sxs-lookup"><span data-stu-id="74b6f-110">Edge</span></span>|
|<span data-ttu-id="74b6f-111">Version</span><span class="sxs-lookup"><span data-stu-id="74b6f-111">Version</span></span>|<span data-ttu-id="74b6f-112">4.6</span><span class="sxs-lookup"><span data-stu-id="74b6f-112">4.6</span></span>|
|<span data-ttu-id="74b6f-113">Type</span><span class="sxs-lookup"><span data-stu-id="74b6f-113">Type</span></span>|<span data-ttu-id="74b6f-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="74b6f-114">Retargeting</span></span>|
