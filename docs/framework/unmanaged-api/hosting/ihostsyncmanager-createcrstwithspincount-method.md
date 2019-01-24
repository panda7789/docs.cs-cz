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
ms.openlocfilehash: 451a5b163499b265396ae2e8f623b448e07ea807
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590913"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="d272a-102">IHostSyncManager::CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="d272a-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="d272a-103">Vytvoří objekt kritický oddíl s počtem typu číselník pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="d272a-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d272a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d272a-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d272a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d272a-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="d272a-106">[in] Určuje počet typu číselník pro objekt kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="d272a-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="d272a-107">[out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci, nebo hodnota null, pokud nebylo možné vytvořit kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="d272a-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d272a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d272a-108">Return Value</span></span>  
  
|<span data-ttu-id="d272a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d272a-109">HRESULT</span></span>|<span data-ttu-id="d272a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d272a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d272a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d272a-111">S_OK</span></span>|<span data-ttu-id="d272a-112">`CreateCrstWithSpinCount` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d272a-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="d272a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d272a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d272a-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d272a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d272a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d272a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d272a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d272a-116">The call timed out.</span></span>|  
|<span data-ttu-id="d272a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d272a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d272a-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d272a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d272a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d272a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d272a-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d272a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d272a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d272a-121">E_FAIL</span></span>|<span data-ttu-id="d272a-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d272a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d272a-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d272a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d272a-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d272a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d272a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d272a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d272a-126">Nedostatek paměti nebyly k dispozici k vytvoření požadované kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="d272a-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d272a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d272a-127">Remarks</span></span>  
 <span data-ttu-id="d272a-128">Počet typu číselník se používá pouze v systému s více procesory.</span><span class="sxs-lookup"><span data-stu-id="d272a-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="d272a-129">Počet typu číselník určuje počet pokusů, které se musí aktivovat volající vlákno, před provedením operace čekání na semafor, který je přidružený k dispozici kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="d272a-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="d272a-130">Pokud během operace typu číselník neuvolní kritický oddíl, volající vlákno se vyhnete operace čekání.</span><span class="sxs-lookup"><span data-stu-id="d272a-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="d272a-131">`CreateCrstWithSpinCount` odráží Win32 `InitializeCriticalSectionAndSpinCount` funkce.</span><span class="sxs-lookup"><span data-stu-id="d272a-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d272a-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d272a-132">Requirements</span></span>  
 <span data-ttu-id="d272a-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d272a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d272a-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d272a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d272a-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d272a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d272a-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d272a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d272a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d272a-137">See also</span></span>
- [<span data-ttu-id="d272a-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d272a-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d272a-139">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d272a-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d272a-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d272a-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
