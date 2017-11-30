---
title: "IHostCrst::SetSpinCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.SetSpinCount
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19172c6d498e5066c102c642105d78d10b26212c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="8d2a7-102">IHostCrst::SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="8d2a7-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="8d2a7-103">Nastaví počet typu číselník pro aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d2a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d2a7-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d2a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d2a7-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="8d2a7-106">[v] Počet nových typu číselník pro aktuální `IHostCrst` instance.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d2a7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d2a7-107">Return Value</span></span>  
  
|<span data-ttu-id="8d2a7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d2a7-108">HRESULT</span></span>|<span data-ttu-id="8d2a7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8d2a7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d2a7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d2a7-110">S_OK</span></span>|<span data-ttu-id="8d2a7-111">`SetSpinCount`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="8d2a7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d2a7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d2a7-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d2a7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d2a7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d2a7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-115">The call timed out.</span></span>|  
|<span data-ttu-id="8d2a7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d2a7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d2a7-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d2a7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d2a7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d2a7-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d2a7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d2a7-120">E_FAIL</span></span>|<span data-ttu-id="8d2a7-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d2a7-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d2a7-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d2a7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d2a7-124">Remarks</span></span>  
 <span data-ttu-id="8d2a7-125">Na systémy s více procesory, pokud kritická sekce reprezentována aktuální `IHostCrst` instance není k dispozici, volající vlákno otáčí `dwSpinCount` časů před volání [ihostsemaphore::wait –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) na semafor přidružené s kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="8d2a7-126">Pokud během operace typu číselník neuvolní části kritické, zabraňuje volající vlákno operace čekání.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="8d2a7-127">Použití `dwSpinCount` je stejný jako při použití parametru se stejným názvem v Win32 `InitializeCriticalSectionAndSpinCount` funkce.</span><span class="sxs-lookup"><span data-stu-id="8d2a7-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d2a7-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d2a7-128">Requirements</span></span>  
 <span data-ttu-id="8d2a7-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d2a7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d2a7-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d2a7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d2a7-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d2a7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d2a7-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d2a7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2a7-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d2a7-133">See Also</span></span>  
 [<span data-ttu-id="8d2a7-134">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d2a7-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8d2a7-135">Ihostcrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d2a7-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="8d2a7-136">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d2a7-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
