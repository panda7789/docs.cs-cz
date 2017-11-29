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
ms.openlocfilehash: 6bc66abf28e90d858d993bd62e9c67f840af137b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="ae083-102">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae083-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="ae083-103">Poskytuje metody pro konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ae083-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae083-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ae083-104">Methods</span></span>  
  
|<span data-ttu-id="ae083-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae083-105">Method</span></span>|<span data-ttu-id="ae083-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ae083-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae083-107">Adddebuggerspecialthread – metoda</span><span class="sxs-lookup"><span data-stu-id="ae083-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="ae083-108">K ladění služby označuje, že konkrétní vlákno by měl povolit chcete pokračovat v provádění ladicí program se zastavila během ladění scénáře spravované nebo nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae083-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="ae083-109">Setdebuggerthreadcontrol – metoda</span><span class="sxs-lookup"><span data-stu-id="ae083-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="ae083-110">Nastaví zpětné volání rozhraní, které ladění služby bude volat jako CLR vláken je blokovaný a odblokováno pro ladění.</span><span class="sxs-lookup"><span data-stu-id="ae083-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="ae083-111">Setgchostcontrol – metoda</span><span class="sxs-lookup"><span data-stu-id="ae083-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="ae083-112">Nastaví zpětné volání rozhraní, které chcete použít modulem garbage collector k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="ae083-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="ae083-113">Setgcthreadcontrol – metoda</span><span class="sxs-lookup"><span data-stu-id="ae083-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="ae083-114">Nastaví zpětné volání rozhraní pro plánování vláken pro úlohy – modul runtime, které by jinak blokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ae083-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae083-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae083-115">Requirements</span></span>  
 <span data-ttu-id="ae083-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae083-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae083-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae083-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae083-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae083-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae083-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae083-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae083-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae083-120">See Also</span></span>  
 [<span data-ttu-id="ae083-121">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="ae083-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="ae083-122">Corruntimehost – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="ae083-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
