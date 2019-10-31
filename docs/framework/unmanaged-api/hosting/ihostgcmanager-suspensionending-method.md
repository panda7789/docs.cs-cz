---
title: IHostGCManager::SuspensionEnding – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 6ef04799c0062c40f1671cbe6d897a148e1b93bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130475"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="9ae60-102">IHostGCManager::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="9ae60-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="9ae60-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) obnovuje spouštění úloh na vláknech, které byly pozastaveny pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9ae60-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ae60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ae60-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ae60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ae60-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="9ae60-106">pro Generování uvolňování paměti, které je právě dokončováno, ze kterého se vlákno obnovuje.</span><span class="sxs-lookup"><span data-stu-id="9ae60-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ae60-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ae60-107">Return Value</span></span>  
  
|<span data-ttu-id="9ae60-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ae60-108">HRESULT</span></span>|<span data-ttu-id="9ae60-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9ae60-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ae60-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ae60-110">S_OK</span></span>|<span data-ttu-id="9ae60-111">`SuspensionEnding` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9ae60-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="9ae60-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ae60-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ae60-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9ae60-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ae60-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ae60-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ae60-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9ae60-115">The call timed out.</span></span>|  
|<span data-ttu-id="9ae60-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ae60-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ae60-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9ae60-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ae60-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ae60-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ae60-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9ae60-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ae60-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ae60-120">E_FAIL</span></span>|<span data-ttu-id="9ae60-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9ae60-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ae60-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9ae60-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ae60-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9ae60-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ae60-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ae60-124">Remarks</span></span>  
 <span data-ttu-id="9ae60-125">Modul CLR volá `SuspensionEnding` poté, co provede uvolňování paměti, aby informoval hostitele, že vlákno pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="9ae60-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9ae60-126">Neměňte plán vlákna, ze kterého byla volána metoda.</span><span class="sxs-lookup"><span data-stu-id="9ae60-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ae60-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ae60-127">Requirements</span></span>  
 <span data-ttu-id="9ae60-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ae60-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ae60-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9ae60-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ae60-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9ae60-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ae60-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ae60-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae60-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ae60-132">See also</span></span>

- [<span data-ttu-id="9ae60-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae60-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9ae60-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae60-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9ae60-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae60-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9ae60-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae60-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="9ae60-137">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ae60-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
