---
title: "IHostSyncManager::CreateSemaphore – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c7e33e4f178a4fd51ae27912959d0e4edf30ecb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="01559-102">IHostSyncManager::CreateSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="01559-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="01559-103">Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objektu pro modul CLR (CLR) má používat jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="01559-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01559-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01559-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01559-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01559-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="01559-106">[v] Počáteční počet `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="01559-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="01559-107">[v] Maximální počet pro `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="01559-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="01559-108">[out] Ukazatel na adresu `IHostSemaphore` instanci, nebo hodnota null, pokud nebylo možné vytvořit semafor.</span><span class="sxs-lookup"><span data-stu-id="01559-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01559-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01559-109">Return Value</span></span>  
  
|<span data-ttu-id="01559-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01559-110">HRESULT</span></span>|<span data-ttu-id="01559-111">Popis</span><span class="sxs-lookup"><span data-stu-id="01559-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01559-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="01559-112">S_OK</span></span>|<span data-ttu-id="01559-113">`CreateSemaphore`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="01559-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="01559-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01559-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01559-115">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="01559-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01559-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01559-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01559-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="01559-117">The call timed out.</span></span>|  
|<span data-ttu-id="01559-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01559-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01559-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="01559-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01559-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01559-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01559-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="01559-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01559-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01559-122">E_FAIL</span></span>|<span data-ttu-id="01559-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="01559-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01559-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="01559-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01559-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01559-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="01559-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="01559-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="01559-127">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="01559-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01559-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01559-128">Remarks</span></span>  
 <span data-ttu-id="01559-129">`CreateSemaphore`zrcadlení Win32 funkce, která má stejný název.</span><span class="sxs-lookup"><span data-stu-id="01559-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="01559-130">`dwInitial` a `dwMax` parametry použít stejnou sémantiku Count semafor jako Win32 `lInitialCount` a `lMaximumCount` parametry, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="01559-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="01559-131">`dwInitial`musí být mezi nulou a `dwMax`(včetně).</span><span class="sxs-lookup"><span data-stu-id="01559-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="01559-132">`dwMax`musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="01559-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01559-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01559-133">Requirements</span></span>  
 <span data-ttu-id="01559-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01559-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01559-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01559-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01559-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01559-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01559-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01559-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01559-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="01559-138">See Also</span></span>  
 [<span data-ttu-id="01559-139">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01559-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="01559-140">Ihostsemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01559-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="01559-141">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01559-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
