---
title: IHostThreadPoolManager::GetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8758bd416b721a95f48b8c8edb933cf617e13455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466490"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="331a3-102">IHostThreadPoolManager::GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="331a3-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="331a3-103">Získá maximální počet vláken, která udržuje hostiteli současně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="331a3-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="331a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="331a3-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="331a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="331a3-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="331a3-106">[out] Ukazatel na maximální počet vláken, která udržuje hostitele ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="331a3-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="331a3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="331a3-107">Return Value</span></span>  
  
|<span data-ttu-id="331a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="331a3-108">HRESULT</span></span>|<span data-ttu-id="331a3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="331a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="331a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="331a3-110">S_OK</span></span>|<span data-ttu-id="331a3-111">`GetMaxThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="331a3-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="331a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="331a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="331a3-113">Modul common language runtime (CLR (nebyl načten do procesu, nebo CLR je ve stavu, ve kterém na ni nelze spustit, spravovaný kód nebo proces volání.</span><span class="sxs-lookup"><span data-stu-id="331a3-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="331a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="331a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="331a3-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="331a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="331a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="331a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="331a3-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="331a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="331a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="331a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="331a3-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="331a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="331a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="331a3-120">E_FAIL</span></span>|<span data-ttu-id="331a3-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="331a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="331a3-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="331a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="331a3-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="331a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="331a3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="331a3-124">E_NOTIMPL</span></span>|<span data-ttu-id="331a3-125">Hostitel neposkytuje implementaci `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="331a3-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="331a3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="331a3-126">Remarks</span></span>  
 <span data-ttu-id="331a3-127">Volání CLR `GetMaxThreads` k určení celkového počtu vláken ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="331a3-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="331a3-128">[Getavailablethreads –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) metoda získá počet vláken, které nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="331a3-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="331a3-129">Všechny požadavky nad vrácenou hodnotou `pdwMaxWorkerThreads` parametr zůstanou ve frontě, dokud vlákna budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="331a3-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="331a3-130">Pokud hostitel neposkytuje implementaci `GetMaxThreads`, měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="331a3-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="331a3-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="331a3-131">Requirements</span></span>  
 <span data-ttu-id="331a3-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="331a3-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="331a3-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="331a3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="331a3-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="331a3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="331a3-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="331a3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331a3-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="331a3-136">See also</span></span>
- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="331a3-137">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="331a3-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="331a3-138">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="331a3-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="331a3-139">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="331a3-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
