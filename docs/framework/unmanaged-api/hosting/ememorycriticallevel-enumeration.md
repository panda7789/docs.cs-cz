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
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774227"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="d1dea-102">EMemoryCriticalLevel – výčet</span><span class="sxs-lookup"><span data-stu-id="d1dea-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="d1dea-103">Obsahuje hodnoty, které označují dopad selhání při přidělování paměti konkrétní se požaduje, ale není možné spokojeni.</span><span class="sxs-lookup"><span data-stu-id="d1dea-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1dea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1dea-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="d1dea-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d1dea-105">Members</span></span>  
  
|<span data-ttu-id="d1dea-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d1dea-106">Member</span></span>|<span data-ttu-id="d1dea-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d1dea-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="d1dea-108">Označuje, že je velmi důležité pro spuštění spravovaného kódu v doméně, která vyžaduje přidělování přidělení.</span><span class="sxs-lookup"><span data-stu-id="d1dea-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="d1dea-109">Pokud nelze přidělit paměť, modul CLR nemůže zaručit, že doménu je stále možné použít.</span><span class="sxs-lookup"><span data-stu-id="d1dea-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="d1dea-110">Hostitele Určuje, jaká akce se má provést při přidělení nedokáže splnit.</span><span class="sxs-lookup"><span data-stu-id="d1dea-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="d1dea-111">To můžete dát pokyn modulu CLR pro přerušení `AppDomain` automaticky, nebo povolíte jeho běžela voláním metod na [iclrpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d1dea-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="d1dea-112">Označuje, že přidělování je zásadní pro spuštění spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="d1dea-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="d1dea-113">Tato hodnota se používá během spouštění a při spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d1dea-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="d1dea-114">Pokud nelze přidělit paměť, modul CLR nelze použít v procesu.</span><span class="sxs-lookup"><span data-stu-id="d1dea-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="d1dea-115">Selhání přidělení paměti CLR efektivně zakázána.</span><span class="sxs-lookup"><span data-stu-id="d1dea-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="d1dea-116">Všechny následné volání do CLR selhat s HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1dea-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="d1dea-117">Označuje, že je důležité pro spuštění úlohy, která vyžaduje přidělování přidělení.</span><span class="sxs-lookup"><span data-stu-id="d1dea-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="d1dea-118">Pokud nelze přidělit paměť, CLR nemůže zaručit, že mohou být provedeny úlohy.</span><span class="sxs-lookup"><span data-stu-id="d1dea-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="d1dea-119">V případě selhání, vydá modul CLR <xref:System.Threading.ThreadAbortException> ve vlákně systému fyzických operace.</span><span class="sxs-lookup"><span data-stu-id="d1dea-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1dea-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1dea-120">Remarks</span></span>  
 <span data-ttu-id="d1dea-121">Metody přidělení paměti definované v [ihostmemorymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) a [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) rozhraní měl parametr tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d1dea-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="d1dea-122">V závislosti na závažnosti k chybě, hostitele můžete rozhodnout, zda požadavek na přidělení selhala okamžitě, nebo počkejte, dokud je možné splnit.</span><span class="sxs-lookup"><span data-stu-id="d1dea-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1dea-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1dea-123">Requirements</span></span>  
 <span data-ttu-id="d1dea-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1dea-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1dea-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1dea-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1dea-126">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1dea-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1dea-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1dea-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1dea-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1dea-128">See also</span></span>

- [<span data-ttu-id="d1dea-129">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1dea-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="d1dea-130">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="d1dea-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
