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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149809"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="6f25e-102">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f25e-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="6f25e-103">Poskytuje metody pro konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6f25e-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f25e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6f25e-104">Methods</span></span>  
  
|<span data-ttu-id="6f25e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f25e-105">Method</span></span>|<span data-ttu-id="6f25e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6f25e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f25e-107">AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="6f25e-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="6f25e-108">Ladění služeb označuje, že konkrétní vlákno by měla být povolena má pokračovat provedením zatímco ladicí program zastavuje během scénáře ladění spravované nebo nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f25e-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="6f25e-109">SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="6f25e-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="6f25e-110">Nastaví rozhraní zpětného volání, které služeb ladění bude volat vlákna modulu CLR jsou blokované a odblokováno pro ladění.</span><span class="sxs-lookup"><span data-stu-id="6f25e-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="6f25e-111">SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="6f25e-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="6f25e-112">Nastaví rozhraní zpětného volání systému uvolňování paměti používané k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="6f25e-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="6f25e-113">SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="6f25e-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="6f25e-114">Nastaví rozhraní zpětného volání pro plánování vláken pro úlohy – modul runtime, které by se jinak zablokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6f25e-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f25e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f25e-115">Requirements</span></span>  
 <span data-ttu-id="6f25e-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f25e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f25e-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f25e-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f25e-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f25e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f25e-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f25e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f25e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f25e-120">See also</span></span>

- [<span data-ttu-id="6f25e-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6f25e-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6f25e-122">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="6f25e-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
