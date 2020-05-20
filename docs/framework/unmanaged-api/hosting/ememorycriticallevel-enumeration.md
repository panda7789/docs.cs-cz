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
ms.openlocfilehash: 248f1d281697923e2da14517ca174fe615bba4ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616200"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="e574f-102">EMemoryCriticalLevel – výčet</span><span class="sxs-lookup"><span data-stu-id="e574f-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="e574f-103">Obsahuje hodnoty, které indikují dopad selhání při požadavku na přidělení konkrétní paměti, ale nelze je splnit.</span><span class="sxs-lookup"><span data-stu-id="e574f-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e574f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e574f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="e574f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e574f-105">Members</span></span>  
  
|<span data-ttu-id="e574f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e574f-106">Member</span></span>|<span data-ttu-id="e574f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e574f-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="e574f-108">Označuje, že přidělení je kritické pro spouštění spravovaného kódu v doméně, která požadovala přidělení.</span><span class="sxs-lookup"><span data-stu-id="e574f-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="e574f-109">Pokud nelze přidělit paměť, CLR nemůže zaručit, že je doména stále použitelná.</span><span class="sxs-lookup"><span data-stu-id="e574f-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="e574f-110">Hostitel rozhodne, jakou akci provést v případě, že přidělení nelze splnit.</span><span class="sxs-lookup"><span data-stu-id="e574f-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="e574f-111">Může vyžádat, aby CLR přerušuje `AppDomain` automaticky, nebo aby mohl být spuštěn voláním metod v [ICLRPolicyManager](iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e574f-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="e574f-112">Označuje, že přidělení je kritické pro spuštění spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="e574f-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="e574f-113">Tato hodnota se používá při spuštění a při spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="e574f-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="e574f-114">Pokud nelze přidělit paměť, modul CLR nemůže v procesu pracovat.</span><span class="sxs-lookup"><span data-stu-id="e574f-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="e574f-115">Pokud se přidělení nepovede, CLR je efektivně zakázaný.</span><span class="sxs-lookup"><span data-stu-id="e574f-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="e574f-116">Všechna následující volání do CLR selžou s HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e574f-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="e574f-117">Indikuje, že přidělení je důležité pro spuštění úlohy, která požadovala přidělení.</span><span class="sxs-lookup"><span data-stu-id="e574f-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="e574f-118">Pokud nelze přidělit paměť, CLR nemůže zaručit, že úlohu lze provést.</span><span class="sxs-lookup"><span data-stu-id="e574f-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="e574f-119">V případě selhání vyvolá CLR ve <xref:System.Threading.ThreadAbortException> vlákně fyzického operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e574f-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e574f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e574f-120">Remarks</span></span>  
 <span data-ttu-id="e574f-121">Metody přidělování paměti definované v rozhraních [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) a [IHostMalloc](ihostmalloc-interface.md) přebírají parametr tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="e574f-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="e574f-122">V závislosti na závažnosti selhání se hostitel může rozhodnout, jestli má požadavek na přidělení selhat okamžitě, nebo počkat, až bude možné ho splnit.</span><span class="sxs-lookup"><span data-stu-id="e574f-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e574f-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e574f-123">Requirements</span></span>  
 <span data-ttu-id="e574f-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e574f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e574f-125">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e574f-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e574f-126">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e574f-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e574f-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e574f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e574f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e574f-128">See also</span></span>

- [<span data-ttu-id="e574f-129">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e574f-129">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="e574f-130">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="e574f-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
