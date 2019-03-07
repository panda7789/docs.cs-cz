---
title: IHostSyncManager::CreateSemaphore – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7c757b941b879cc63d1b3e2ec1f3b9396193f6d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479386"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="77975-102">IHostSyncManager::CreateSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="77975-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="77975-103">Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objektu pro common language runtime (CLR) má používat jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="77975-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77975-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77975-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77975-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77975-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="77975-106">[in] Počáteční počet pro `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="77975-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="77975-107">[in] Maximální počet pro `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="77975-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="77975-108">[out] Ukazatel na adresu `IHostSemaphore` instanci, nebo hodnota null, pokud nebylo možné vytvořit semafor.</span><span class="sxs-lookup"><span data-stu-id="77975-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77975-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="77975-109">Return Value</span></span>  
  
|<span data-ttu-id="77975-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77975-110">HRESULT</span></span>|<span data-ttu-id="77975-111">Popis</span><span class="sxs-lookup"><span data-stu-id="77975-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77975-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="77975-112">S_OK</span></span>|<span data-ttu-id="77975-113">`CreateSemaphore` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="77975-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="77975-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77975-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77975-115">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="77975-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77975-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77975-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77975-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="77975-117">The call timed out.</span></span>|  
|<span data-ttu-id="77975-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77975-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77975-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="77975-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77975-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77975-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77975-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="77975-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77975-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77975-122">E_FAIL</span></span>|<span data-ttu-id="77975-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="77975-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77975-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="77975-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77975-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77975-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77975-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="77975-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="77975-127">Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.</span><span class="sxs-lookup"><span data-stu-id="77975-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77975-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77975-128">Remarks</span></span>  
 <span data-ttu-id="77975-129">`CreateSemaphore` Zrcadlí funkci Win32, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="77975-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="77975-130">`dwInitial` a `dwMax` parametry použít stejnou sémantiku počtu pro semafor jako Win32 `lInitialCount` a `lMaximumCount` parametry, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="77975-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="77975-131">`dwInitial` musí být mezi nulou a `dwMax`včetně.</span><span class="sxs-lookup"><span data-stu-id="77975-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="77975-132">`dwMax` Musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="77975-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77975-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77975-133">Requirements</span></span>  
 <span data-ttu-id="77975-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77975-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77975-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77975-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77975-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77975-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77975-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77975-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77975-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77975-138">See also</span></span>
- [<span data-ttu-id="77975-139">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77975-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="77975-140">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77975-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="77975-141">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77975-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
