---
title: IHostSemaphore::ReleaseSemaphore – metoda
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 580603bf04afe353aeb124a8c1e548d897033d23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652836"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="c6edf-102">IHostSemaphore::ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="c6edf-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="c6edf-103">Zvýší počet aktuální [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance podle zadaného množství.</span><span class="sxs-lookup"><span data-stu-id="c6edf-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6edf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6edf-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6edf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6edf-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="c6edf-106">[in] Rozsah, pomocí kterého zvýšit počet aktuální `IHostSemaphore` instance.</span><span class="sxs-lookup"><span data-stu-id="c6edf-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="c6edf-107">Šířka musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="c6edf-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="c6edf-108">[out] Ukazatel na počet předchozího nebo hodnota null, pokud volající nevyžaduje předchozího počtu.</span><span class="sxs-lookup"><span data-stu-id="c6edf-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6edf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6edf-109">Return Value</span></span>  
  
|<span data-ttu-id="c6edf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6edf-110">HRESULT</span></span>|<span data-ttu-id="c6edf-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c6edf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6edf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6edf-112">S_OK</span></span>|<span data-ttu-id="c6edf-113">`ReleaseSemaphore` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c6edf-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="c6edf-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6edf-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6edf-115">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c6edf-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6edf-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6edf-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6edf-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c6edf-117">The call timed out.</span></span>|  
|<span data-ttu-id="c6edf-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6edf-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6edf-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c6edf-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6edf-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6edf-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6edf-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c6edf-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6edf-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6edf-122">E_FAIL</span></span>|<span data-ttu-id="c6edf-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c6edf-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6edf-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c6edf-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6edf-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6edf-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6edf-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6edf-126">Remarks</span></span>  
 <span data-ttu-id="c6edf-127">CLR volá obvykle `ReleaseSemaphore` aby upozornil hostitele, že byla dokončena prostředek, předejte hodnotu 1 pro použití `lReleaseCount` parametru.</span><span class="sxs-lookup"><span data-stu-id="c6edf-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6edf-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6edf-128">Requirements</span></span>  
 <span data-ttu-id="c6edf-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6edf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6edf-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6edf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6edf-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6edf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6edf-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6edf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6edf-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6edf-133">See also</span></span>
- [<span data-ttu-id="c6edf-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6edf-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c6edf-135">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6edf-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="c6edf-136">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6edf-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="c6edf-137">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6edf-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="c6edf-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6edf-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
