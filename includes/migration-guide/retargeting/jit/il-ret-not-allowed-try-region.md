---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615637"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="6ceda-101">V oblasti try není povolená technologie IL ret</span><span class="sxs-lookup"><span data-stu-id="6ceda-101">IL ret not allowed in a try region</span></span>

#### <a name="details"></a><span data-ttu-id="6ceda-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6ceda-102">Details</span></span>

<span data-ttu-id="6ceda-103">Na rozdíl od JIT64 kompilátoru za běhu nepovoluje RyuJIT (používá se v .NET Framework 4,6) instrukci IL v oblasti try.</span><span class="sxs-lookup"><span data-stu-id="6ceda-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="6ceda-104">Vrácení z oblasti try není povoleno specifikací ECMA-335 a žádný známý spravovaný kompilátor takové IL negeneruje.</span><span class="sxs-lookup"><span data-stu-id="6ceda-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="6ceda-105">Nicméně kompilátor JIT64 spustí takové IL, pokud je vygenerován pomocí generování reflexe.</span><span class="sxs-lookup"><span data-stu-id="6ceda-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6ceda-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="6ceda-106">Suggestion</span></span>

<span data-ttu-id="6ceda-107">Pokud aplikace generuje IL, která zahrnuje ret v oblasti try, aplikace může cílit .NET Framework 4,5, aby používala starou JIT a zabránila tomuto přerušení.</span><span class="sxs-lookup"><span data-stu-id="6ceda-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="6ceda-108">Případně je možné vygenerované IL aktualizovat, aby se vracely po oblasti try.</span><span class="sxs-lookup"><span data-stu-id="6ceda-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>

| <span data-ttu-id="6ceda-109">Name</span><span class="sxs-lookup"><span data-stu-id="6ceda-109">Name</span></span>    | <span data-ttu-id="6ceda-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ceda-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ceda-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6ceda-111">Scope</span></span>   | <span data-ttu-id="6ceda-112">Edge</span><span class="sxs-lookup"><span data-stu-id="6ceda-112">Edge</span></span>        |
| <span data-ttu-id="6ceda-113">Verze</span><span class="sxs-lookup"><span data-stu-id="6ceda-113">Version</span></span> | <span data-ttu-id="6ceda-114">4.6</span><span class="sxs-lookup"><span data-stu-id="6ceda-114">4.6</span></span>         |
| <span data-ttu-id="6ceda-115">Typ</span><span class="sxs-lookup"><span data-stu-id="6ceda-115">Type</span></span>    | <span data-ttu-id="6ceda-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="6ceda-116">Retargeting</span></span> |
