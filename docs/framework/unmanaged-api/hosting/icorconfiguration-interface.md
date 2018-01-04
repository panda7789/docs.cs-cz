---
title: "ICorConfiguration – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorConfiguration
helpviewer_keywords: ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af9a7d4bb1d38fd4a81e954074b074325409ee5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="dadea-102">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dadea-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="dadea-103">Poskytuje metody pro konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="dadea-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dadea-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dadea-104">Methods</span></span>  
  
|<span data-ttu-id="dadea-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dadea-105">Method</span></span>|<span data-ttu-id="dadea-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dadea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dadea-107">AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="dadea-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="dadea-108">K ladění služby označuje, že konkrétní vlákno by měl povolit chcete pokračovat v provádění ladicí program se zastavila během ladění scénáře spravované nebo nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="dadea-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="dadea-109">SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="dadea-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="dadea-110">Nastaví zpětné volání rozhraní, které ladění služby bude volat jako CLR vláken je blokovaný a odblokováno pro ladění.</span><span class="sxs-lookup"><span data-stu-id="dadea-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="dadea-111">SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="dadea-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="dadea-112">Nastaví zpětné volání rozhraní, které chcete použít modulem garbage collector k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="dadea-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="dadea-113">SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="dadea-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="dadea-114">Nastaví zpětné volání rozhraní pro plánování vláken pro úlohy – modul runtime, které by jinak blokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="dadea-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dadea-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dadea-115">Requirements</span></span>  
 <span data-ttu-id="dadea-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dadea-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dadea-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dadea-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dadea-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dadea-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dadea-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dadea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dadea-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dadea-120">See Also</span></span>  
 [<span data-ttu-id="dadea-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="dadea-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="dadea-122">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="dadea-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
