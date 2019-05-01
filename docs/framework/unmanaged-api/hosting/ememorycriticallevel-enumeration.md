---
title: EMemoryCriticalLevel – výčet
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee8705d00e1f63f69863d0bf8e7d0d9d62807e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968598"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="50434-102">EMemoryCriticalLevel – výčet</span><span class="sxs-lookup"><span data-stu-id="50434-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="50434-103">Obsahuje hodnoty, které označují dopad selhání při přidělování paměti konkrétní se požaduje, ale není možné spokojeni.</span><span class="sxs-lookup"><span data-stu-id="50434-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50434-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50434-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="50434-105">Členové</span><span class="sxs-lookup"><span data-stu-id="50434-105">Members</span></span>  
  
|<span data-ttu-id="50434-106">Člen</span><span class="sxs-lookup"><span data-stu-id="50434-106">Member</span></span>|<span data-ttu-id="50434-107">Popis</span><span class="sxs-lookup"><span data-stu-id="50434-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="50434-108">Označuje, že je velmi důležité pro spuštění spravovaného kódu v doméně, která vyžaduje přidělování přidělení.</span><span class="sxs-lookup"><span data-stu-id="50434-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="50434-109">Pokud nelze přidělit paměť, modul CLR nemůže zaručit, že doménu je stále možné použít.</span><span class="sxs-lookup"><span data-stu-id="50434-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="50434-110">Hostitele Určuje, jaká akce se má provést při přidělení nedokáže splnit.</span><span class="sxs-lookup"><span data-stu-id="50434-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="50434-111">To můžete dát pokyn modulu CLR pro přerušení `AppDomain` automaticky, nebo povolíte jeho běžela voláním metod na [iclrpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="50434-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="50434-112">Označuje, že přidělování je zásadní pro spuštění spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="50434-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="50434-113">Tato hodnota se používá během spouštění a při spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="50434-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="50434-114">Pokud nelze přidělit paměť, modul CLR nelze použít v procesu.</span><span class="sxs-lookup"><span data-stu-id="50434-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="50434-115">Selhání přidělení paměti CLR efektivně zakázána.</span><span class="sxs-lookup"><span data-stu-id="50434-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="50434-116">Všechny následné volání do CLR selhat s HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50434-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="50434-117">Označuje, že je důležité pro spuštění úlohy, která vyžaduje přidělování přidělení.</span><span class="sxs-lookup"><span data-stu-id="50434-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="50434-118">Pokud nelze přidělit paměť, CLR nemůže zaručit, že mohou být provedeny úlohy.</span><span class="sxs-lookup"><span data-stu-id="50434-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="50434-119">V případě selhání, vydá modul CLR <xref:System.Threading.ThreadAbortException> ve vlákně systému fyzických operace.</span><span class="sxs-lookup"><span data-stu-id="50434-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50434-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50434-120">Remarks</span></span>  
 <span data-ttu-id="50434-121">Metody přidělení paměti definované v [ihostmemorymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) a [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) rozhraní měl parametr tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="50434-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="50434-122">V závislosti na závažnosti k chybě, hostitele můžete rozhodnout, zda požadavek na přidělení selhala okamžitě, nebo počkejte, dokud je možné splnit.</span><span class="sxs-lookup"><span data-stu-id="50434-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50434-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50434-123">Requirements</span></span>  
 <span data-ttu-id="50434-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50434-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50434-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50434-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50434-126">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50434-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50434-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50434-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50434-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50434-128">See also</span></span>

- [<span data-ttu-id="50434-129">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50434-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="50434-130">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="50434-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
