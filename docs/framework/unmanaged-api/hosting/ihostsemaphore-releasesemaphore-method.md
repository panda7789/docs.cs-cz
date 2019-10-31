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
ms.openlocfilehash: 33a92365e7765befe669439eabefac607232ff15
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139462"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="8301e-102">IHostSemaphore::ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="8301e-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="8301e-103">Zvýší počet aktuálních instancí [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) o zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8301e-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8301e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8301e-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8301e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8301e-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="8301e-106">pro Hodnota, o kterou se má zvýšit počet aktuální instance `IHostSemaphore`</span><span class="sxs-lookup"><span data-stu-id="8301e-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="8301e-107">Tato hodnota musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="8301e-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="8301e-108">mimo Ukazatel na předchozí počet nebo hodnotu null, pokud volající nevyžaduje předchozí počet.</span><span class="sxs-lookup"><span data-stu-id="8301e-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8301e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8301e-109">Return Value</span></span>  
  
|<span data-ttu-id="8301e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8301e-110">HRESULT</span></span>|<span data-ttu-id="8301e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8301e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8301e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8301e-112">S_OK</span></span>|<span data-ttu-id="8301e-113">`ReleaseSemaphore` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8301e-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="8301e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8301e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8301e-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8301e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8301e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8301e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8301e-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8301e-117">The call timed out.</span></span>|  
|<span data-ttu-id="8301e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8301e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8301e-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8301e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8301e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8301e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8301e-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8301e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8301e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8301e-122">E_FAIL</span></span>|<span data-ttu-id="8301e-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8301e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8301e-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8301e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8301e-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8301e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8301e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8301e-126">Remarks</span></span>  
 <span data-ttu-id="8301e-127">Modul CLR obvykle volá `ReleaseSemaphore`, aby upozornil hostitele, že dokončil použití prostředku, a předáním hodnoty 1 pro parametr `lReleaseCount`.</span><span class="sxs-lookup"><span data-stu-id="8301e-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8301e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8301e-128">Requirements</span></span>  
 <span data-ttu-id="8301e-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8301e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8301e-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8301e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8301e-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8301e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8301e-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8301e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8301e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8301e-133">See also</span></span>

- [<span data-ttu-id="8301e-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8301e-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8301e-135">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8301e-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="8301e-136">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8301e-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="8301e-137">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8301e-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="8301e-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8301e-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
