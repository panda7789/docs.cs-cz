---
title: ICorConfiguration – rozhraní
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: 3b8c9421dea4040a9f183b886f1ad8575cace780
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762423"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="f003f-102">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f003f-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="f003f-103">Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f003f-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f003f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f003f-104">Methods</span></span>  
  
|<span data-ttu-id="f003f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f003f-105">Method</span></span>|<span data-ttu-id="f003f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f003f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f003f-107">AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="f003f-107">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="f003f-108">Označuje ladicí služby, že by mělo být povoleno pokračování v provádění určitého vlákna, zatímco ladicí program aplikace zastavil během spravovaných nebo nespravovaných scénářů ladění.</span><span class="sxs-lookup"><span data-stu-id="f003f-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="f003f-109">SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="f003f-109">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="f003f-110">Nastaví rozhraní zpětného volání, které budou ladit služby volání jako vlákna CLR, jsou blokovány a odblokovány pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f003f-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="f003f-111">SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="f003f-111">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="f003f-112">Nastaví rozhraní zpětného volání, které má systém uvolňování paměti použít k vyžádání hostitele, aby změnil limity virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="f003f-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="f003f-113">SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="f003f-113">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="f003f-114">Nastaví rozhraní zpětného volání pro plánování vláken pro neběhové úlohy, které by jinak bylo zablokováno pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f003f-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f003f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f003f-115">Requirements</span></span>  
 <span data-ttu-id="f003f-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f003f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f003f-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f003f-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f003f-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f003f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f003f-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f003f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f003f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f003f-120">See also</span></span>

- [<span data-ttu-id="f003f-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f003f-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f003f-122">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="f003f-122">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
