---
title: "IHostSyncManager::CreateCrst – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b54abb60b00d071900d3bfdd01c2e5f1807998a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="0c1c0-102">IHostSyncManager::CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="0c1c0-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="0c1c0-103">Vytvoří objekt kritická sekce modulu pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c1c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c1c0-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c1c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c1c0-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="0c1c0-106">[out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci implementované pro hostitele, nebo hodnotu null, pokud nebylo možné vytvořit kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c1c0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0c1c0-107">Return Value</span></span>  
  
|<span data-ttu-id="0c1c0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c1c0-108">HRESULT</span></span>|<span data-ttu-id="0c1c0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0c1c0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c1c0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c1c0-110">S_OK</span></span>|<span data-ttu-id="0c1c0-111">`CreateCrst`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="0c1c0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c1c0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c1c0-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c1c0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c1c0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c1c0-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c1c0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c1c0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c1c0-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c1c0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c1c0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c1c0-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c1c0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c1c0-120">E_FAIL</span></span>|<span data-ttu-id="0c1c0-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c1c0-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c1c0-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0c1c0-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0c1c0-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0c1c0-125">Nedostatek paměti nebylo k dispozici pro její vytvoření požadovaný kritické.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c1c0-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c1c0-126">Remarks</span></span>  
 <span data-ttu-id="0c1c0-127">Kritická sekce objekty poskytují synchronizace podobná poskytované objekt mutex, s tím rozdílem, že kritické oddíly mohou být používány pouze vláken v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="0c1c0-128">`CreateCrst`odpovídá Win32 `InitializeCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="0c1c0-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c1c0-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c1c0-129">Requirements</span></span>  
 <span data-ttu-id="0c1c0-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c1c0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c1c0-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c1c0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c1c0-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c1c0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c1c0-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c1c0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c1c0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c1c0-134">See Also</span></span>  
 [<span data-ttu-id="0c1c0-135">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c1c0-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0c1c0-136">Ihostcrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c1c0-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="0c1c0-137">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c1c0-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="0c1c0-138">Ihostsemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c1c0-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="0c1c0-139">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="0c1c0-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="0c1c0-140">Semafor a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="0c1c0-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
