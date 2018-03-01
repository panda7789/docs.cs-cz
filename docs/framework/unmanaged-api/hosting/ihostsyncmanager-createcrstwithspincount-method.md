---
title: "IHostSyncManager::CreateCrstWithSpinCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31830f97cff1c302ee573b8248eb1d83e696ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="7adf9-102">IHostSyncManager::CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7adf9-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="7adf9-103">Vytvoří objekt kritická sekce s počtem typu číselník pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="7adf9-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7adf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7adf9-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7adf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7adf9-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="7adf9-106">[v] Určuje počet typu číselník pro objekt kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="7adf9-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="7adf9-107">[out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci, nebo hodnota null, pokud nebylo možné vytvořit kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="7adf9-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7adf9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7adf9-108">Return Value</span></span>  
  
|<span data-ttu-id="7adf9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7adf9-109">HRESULT</span></span>|<span data-ttu-id="7adf9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7adf9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7adf9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7adf9-111">S_OK</span></span>|<span data-ttu-id="7adf9-112">`CreateCrstWithSpinCount`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7adf9-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="7adf9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7adf9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7adf9-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7adf9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7adf9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7adf9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7adf9-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7adf9-116">The call timed out.</span></span>|  
|<span data-ttu-id="7adf9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7adf9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7adf9-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="7adf9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7adf9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7adf9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7adf9-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="7adf9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7adf9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7adf9-121">E_FAIL</span></span>|<span data-ttu-id="7adf9-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="7adf9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7adf9-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7adf9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7adf9-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7adf9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7adf9-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7adf9-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7adf9-126">Nedostatek paměti nebylo k dispozici pro její vytvoření požadovaný kritické.</span><span class="sxs-lookup"><span data-stu-id="7adf9-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7adf9-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7adf9-127">Remarks</span></span>  
 <span data-ttu-id="7adf9-128">Počet otočení se používá pouze v systému s více procesory.</span><span class="sxs-lookup"><span data-stu-id="7adf9-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="7adf9-129">Počet typu číselník určuje počet opakovaných volající vlákno musí číselníku před provedením operace čekání na semafor, který je přidružen k dispozici kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="7adf9-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="7adf9-130">Pokud během operace typu číselník neuvolní části kritické, zabraňuje volající vlákno operace čekání.</span><span class="sxs-lookup"><span data-stu-id="7adf9-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="7adf9-131">`CreateCrstWithSpinCount`odpovídá Win32 `InitializeCriticalSectionAndSpinCount` funkce.</span><span class="sxs-lookup"><span data-stu-id="7adf9-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7adf9-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7adf9-132">Requirements</span></span>  
 <span data-ttu-id="7adf9-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7adf9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7adf9-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7adf9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7adf9-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7adf9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7adf9-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7adf9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7adf9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7adf9-137">See Also</span></span>  
 [<span data-ttu-id="7adf9-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7adf9-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7adf9-139">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7adf9-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="7adf9-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7adf9-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
