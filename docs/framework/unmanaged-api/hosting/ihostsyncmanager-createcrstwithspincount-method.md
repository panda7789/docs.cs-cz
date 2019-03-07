---
title: IHostSyncManager::CreateCrstWithSpinCount – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4dd73efbad5ffac47c8585facd1717d77147fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501578"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="c9a6c-102">IHostSyncManager::CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="c9a6c-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="c9a6c-103">Vytvoří objekt kritický oddíl s počtem typu číselník pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9a6c-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9a6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9a6c-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="c9a6c-106">[in] Určuje počet typu číselník pro objekt kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="c9a6c-107">[out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci, nebo hodnota null, pokud nebylo možné vytvořit kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9a6c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9a6c-108">Return Value</span></span>  
  
|<span data-ttu-id="c9a6c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9a6c-109">HRESULT</span></span>|<span data-ttu-id="c9a6c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c9a6c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9a6c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9a6c-111">S_OK</span></span>|<span data-ttu-id="c9a6c-112">`CreateCrstWithSpinCount` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="c9a6c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9a6c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9a6c-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9a6c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9a6c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9a6c-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-116">The call timed out.</span></span>|  
|<span data-ttu-id="c9a6c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9a6c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9a6c-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9a6c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9a6c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9a6c-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9a6c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9a6c-121">E_FAIL</span></span>|<span data-ttu-id="c9a6c-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9a6c-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9a6c-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9a6c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c9a6c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c9a6c-126">Nedostatek paměti nebyly k dispozici k vytvoření požadované kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9a6c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9a6c-127">Remarks</span></span>  
 <span data-ttu-id="c9a6c-128">Počet typu číselník se používá pouze v systému s více procesory.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="c9a6c-129">Počet typu číselník určuje počet pokusů, které se musí aktivovat volající vlákno, před provedením operace čekání na semafor, který je přidružený k dispozici kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="c9a6c-130">Pokud během operace typu číselník neuvolní kritický oddíl, volající vlákno se vyhnete operace čekání.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="c9a6c-131">`CreateCrstWithSpinCount` odráží Win32 `InitializeCriticalSectionAndSpinCount` funkce.</span><span class="sxs-lookup"><span data-stu-id="c9a6c-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9a6c-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9a6c-132">Requirements</span></span>  
 <span data-ttu-id="c9a6c-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9a6c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9a6c-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9a6c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9a6c-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9a6c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9a6c-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9a6c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a6c-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9a6c-137">See also</span></span>
- [<span data-ttu-id="c9a6c-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9a6c-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c9a6c-139">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9a6c-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="c9a6c-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9a6c-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
