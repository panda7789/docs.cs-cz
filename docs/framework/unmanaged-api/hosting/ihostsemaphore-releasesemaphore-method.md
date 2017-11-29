---
title: "IHostSemaphore::ReleaseSemaphore – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore.ReleaseSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06765d019d5443730656e7f4d6745bd8ad39ee00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="f3130-102">IHostSemaphore::ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="f3130-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="f3130-103">Zvyšuje počet aktuální [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instanci zadanou velikost.</span><span class="sxs-lookup"><span data-stu-id="f3130-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3130-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3130-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3130-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="f3130-106">[v] Hodnota, o které se zvýší počet aktuální `IHostSemaphore` instance.</span><span class="sxs-lookup"><span data-stu-id="f3130-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="f3130-107">Toto množství musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="f3130-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="f3130-108">[out] Ukazatel na předchozí count nebo hodnota null, pokud má volající nevyžaduje předchozí počet.</span><span class="sxs-lookup"><span data-stu-id="f3130-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3130-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f3130-109">Return Value</span></span>  
  
|<span data-ttu-id="f3130-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3130-110">HRESULT</span></span>|<span data-ttu-id="f3130-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f3130-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3130-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3130-112">S_OK</span></span>|<span data-ttu-id="f3130-113">`ReleaseSemaphore`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f3130-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="f3130-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3130-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3130-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f3130-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3130-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3130-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3130-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f3130-117">The call timed out.</span></span>|  
|<span data-ttu-id="f3130-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3130-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3130-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="f3130-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3130-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3130-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3130-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="f3130-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3130-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3130-122">E_FAIL</span></span>|<span data-ttu-id="f3130-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f3130-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3130-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f3130-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3130-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f3130-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3130-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3130-126">Remarks</span></span>  
 <span data-ttu-id="f3130-127">Modul CLR obvykle volá `ReleaseSemaphore` hostitele oznámit, že byla dokončena pomocí prostředku, na hodnotu 1 pro předávání `lReleaseCount` parametr.</span><span class="sxs-lookup"><span data-stu-id="f3130-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3130-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3130-128">Requirements</span></span>  
 <span data-ttu-id="f3130-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3130-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3130-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3130-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3130-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3130-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3130-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3130-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3130-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3130-133">See Also</span></span>  
 [<span data-ttu-id="f3130-134">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3130-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f3130-135">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3130-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="f3130-136">Ihostmanualevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3130-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="f3130-137">Ihostsemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3130-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="f3130-138">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3130-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
