---
title: IHostCrst::SetSpinCount – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf83c7755bc099275c02ff0049f663573c582faf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469558"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="4407b-102">IHostCrst::SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="4407b-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="4407b-103">Nastaví počet typu číselník pro aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="4407b-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4407b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4407b-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4407b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4407b-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="4407b-106">[in] Nový počet typu číselník pro aktuální `IHostCrst` instance.</span><span class="sxs-lookup"><span data-stu-id="4407b-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4407b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4407b-107">Return Value</span></span>  
  
|<span data-ttu-id="4407b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4407b-108">HRESULT</span></span>|<span data-ttu-id="4407b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4407b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4407b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4407b-110">S_OK</span></span>|<span data-ttu-id="4407b-111">`SetSpinCount` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4407b-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="4407b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4407b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4407b-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4407b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4407b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4407b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4407b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4407b-115">The call timed out.</span></span>|  
|<span data-ttu-id="4407b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4407b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4407b-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="4407b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4407b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4407b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4407b-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="4407b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4407b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4407b-120">E_FAIL</span></span>|<span data-ttu-id="4407b-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="4407b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4407b-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4407b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4407b-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4407b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4407b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4407b-124">Remarks</span></span>  
 <span data-ttu-id="4407b-125">Na více procesorů systémech, pokud kritický oddíl reprezentována aktuální `IHostCrst` instance není k dispozici, volající vlákno přede `dwSpinCount` doby před voláním [ihostsemaphore::wait –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) na semaforu související s kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="4407b-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="4407b-126">Pokud během operace typu číselník neuvolní kritický oddíl, volající vlákno se vyhnete operace čekání.</span><span class="sxs-lookup"><span data-stu-id="4407b-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="4407b-127">Použití `dwSpinCount` je stejný jako použití parametru se stejným názvem v Win32 `InitializeCriticalSectionAndSpinCount` funkce.</span><span class="sxs-lookup"><span data-stu-id="4407b-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4407b-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4407b-128">Requirements</span></span>  
 <span data-ttu-id="4407b-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4407b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4407b-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4407b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4407b-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4407b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4407b-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4407b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4407b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4407b-133">See also</span></span>
- [<span data-ttu-id="4407b-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4407b-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4407b-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4407b-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="4407b-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4407b-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
