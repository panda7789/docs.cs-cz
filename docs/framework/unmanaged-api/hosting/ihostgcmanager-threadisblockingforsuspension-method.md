---
title: IHostGCManager::ThreadIsBlockingForSuspension – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: cb807a6a344c49baeedfa88aef989a9cb2ec8a46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133921"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="48b75-102">IHostGCManager::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="48b75-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="48b75-103">Upozorní hostitele, že vlákno, ze kterého bylo volání metody provedeno, bude zablokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="48b75-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48b75-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="48b75-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="48b75-105">Return Value</span></span>  
  
|<span data-ttu-id="48b75-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48b75-106">HRESULT</span></span>|<span data-ttu-id="48b75-107">Popis</span><span class="sxs-lookup"><span data-stu-id="48b75-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48b75-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="48b75-108">S_OK</span></span>|<span data-ttu-id="48b75-109">`ThreadIsBlockingForSuspension` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="48b75-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="48b75-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48b75-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48b75-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="48b75-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48b75-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48b75-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48b75-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="48b75-113">The call timed out.</span></span>|  
|<span data-ttu-id="48b75-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48b75-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48b75-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="48b75-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48b75-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48b75-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48b75-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="48b75-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48b75-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48b75-118">E_FAIL</span></span>|<span data-ttu-id="48b75-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="48b75-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48b75-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="48b75-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48b75-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="48b75-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48b75-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48b75-122">Remarks</span></span>  
 <span data-ttu-id="48b75-123">CLR obvykle volá metodu `ThreadIsBlockForSuspension` v přípravě na uvolňování paměti, aby bylo možné hostiteli dát možnost znovu naplánovat vlákno pro nespravované úlohy.</span><span class="sxs-lookup"><span data-stu-id="48b75-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48b75-124">Hostitel může znovu naplánovat úlohy až po volání `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="48b75-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="48b75-125">Po volání za běhu [SuspensionStarting –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)hostitel nesmí znovu naplánovat úlohu.</span><span class="sxs-lookup"><span data-stu-id="48b75-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b75-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48b75-126">Requirements</span></span>  
 <span data-ttu-id="48b75-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b75-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b75-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48b75-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48b75-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48b75-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48b75-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b75-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b75-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48b75-131">See also</span></span>

- [<span data-ttu-id="48b75-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48b75-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="48b75-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48b75-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="48b75-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48b75-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="48b75-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48b75-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="48b75-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48b75-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
