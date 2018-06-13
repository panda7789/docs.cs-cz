---
title: IHostSyncManager::CreateCrst – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101a652aa77e587003fb7e773e00ba9b77461a06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441890"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="6237c-102">IHostSyncManager::CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="6237c-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="6237c-103">Vytvoří objekt kritická sekce modulu pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="6237c-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6237c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6237c-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6237c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6237c-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="6237c-106">[out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci implementované pro hostitele, nebo hodnotu null, pokud nebylo možné vytvořit kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="6237c-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6237c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6237c-107">Return Value</span></span>  
  
|<span data-ttu-id="6237c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6237c-108">HRESULT</span></span>|<span data-ttu-id="6237c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6237c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6237c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6237c-110">S_OK</span></span>|<span data-ttu-id="6237c-111">`CreateCrst` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6237c-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="6237c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6237c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6237c-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6237c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6237c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6237c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6237c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6237c-115">The call timed out.</span></span>|  
|<span data-ttu-id="6237c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6237c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6237c-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="6237c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6237c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6237c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6237c-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="6237c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6237c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6237c-120">E_FAIL</span></span>|<span data-ttu-id="6237c-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="6237c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6237c-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6237c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6237c-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6237c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6237c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6237c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6237c-125">Nedostatek paměti nebylo k dispozici pro její vytvoření požadovaný kritické.</span><span class="sxs-lookup"><span data-stu-id="6237c-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6237c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6237c-126">Remarks</span></span>  
 <span data-ttu-id="6237c-127">Kritická sekce objekty poskytují synchronizace podobná poskytované objekt mutex, s tím rozdílem, že kritické oddíly mohou být používány pouze vláken v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="6237c-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="6237c-128">`CreateCrst` odpovídá Win32 `InitializeCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="6237c-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6237c-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6237c-129">Requirements</span></span>  
 <span data-ttu-id="6237c-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6237c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6237c-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6237c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6237c-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6237c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6237c-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6237c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6237c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6237c-134">See Also</span></span>  
 [<span data-ttu-id="6237c-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6237c-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6237c-136">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6237c-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="6237c-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6237c-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="6237c-138">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6237c-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="6237c-139">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="6237c-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="6237c-140">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="6237c-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
