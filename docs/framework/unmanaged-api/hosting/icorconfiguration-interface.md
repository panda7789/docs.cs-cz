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
ms.openlocfilehash: 80bb68486e555d6c96cf8ee56ed6d60e41c7c5c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127806"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="699b3-102">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="699b3-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="699b3-103">Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="699b3-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="699b3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="699b3-104">Methods</span></span>  
  
|<span data-ttu-id="699b3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="699b3-105">Method</span></span>|<span data-ttu-id="699b3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="699b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="699b3-107">AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="699b3-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="699b3-108">Označuje ladicí služby, že by mělo být povoleno pokračování v provádění určitého vlákna, zatímco ladicí program aplikace zastavil během spravovaných nebo nespravovaných scénářů ladění.</span><span class="sxs-lookup"><span data-stu-id="699b3-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="699b3-109">SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="699b3-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="699b3-110">Nastaví rozhraní zpětného volání, které budou ladit služby volání jako vlákna CLR, jsou blokovány a odblokovány pro ladění.</span><span class="sxs-lookup"><span data-stu-id="699b3-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="699b3-111">SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="699b3-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="699b3-112">Nastaví rozhraní zpětného volání, které má systém uvolňování paměti použít k vyžádání hostitele, aby změnil limity virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="699b3-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="699b3-113">SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="699b3-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="699b3-114">Nastaví rozhraní zpětného volání pro plánování vláken pro neběhové úlohy, které by jinak bylo zablokováno pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="699b3-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="699b3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="699b3-115">Requirements</span></span>  
 <span data-ttu-id="699b3-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="699b3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="699b3-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="699b3-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="699b3-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="699b3-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="699b3-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="699b3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699b3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="699b3-120">See also</span></span>

- [<span data-ttu-id="699b3-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="699b3-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="699b3-122">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="699b3-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
