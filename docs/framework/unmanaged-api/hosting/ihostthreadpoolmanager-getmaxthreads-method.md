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
ms.openlocfilehash: e53265556de026e84af7ca345a5f82be3c5ff812
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122059"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="7150d-102">IHostThreadPoolManager::GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="7150d-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="7150d-103">Získá maximální počet vláken, která hostitel udržuje souběžně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="7150d-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7150d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7150d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7150d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7150d-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="7150d-106">mimo Ukazatel na maximální počet vláken, která hostitel udržuje ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="7150d-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7150d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7150d-107">Return Value</span></span>  
  
|<span data-ttu-id="7150d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7150d-108">HRESULT</span></span>|<span data-ttu-id="7150d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7150d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7150d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7150d-110">S_OK</span></span>|<span data-ttu-id="7150d-111">`GetMaxThreads` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7150d-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="7150d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7150d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7150d-113">Modul CLR (Common Language Runtime) (CLR (nebyl načten do procesu) nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7150d-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7150d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7150d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7150d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7150d-115">The call timed out.</span></span>|  
|<span data-ttu-id="7150d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7150d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7150d-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7150d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7150d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7150d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7150d-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7150d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7150d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7150d-120">E_FAIL</span></span>|<span data-ttu-id="7150d-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7150d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7150d-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7150d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7150d-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7150d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7150d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7150d-124">E_NOTIMPL</span></span>|<span data-ttu-id="7150d-125">Hostitel neposkytuje implementaci `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="7150d-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7150d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7150d-126">Remarks</span></span>  
 <span data-ttu-id="7150d-127">CLR volá `GetMaxThreads` k určení celkového počtu vláken ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="7150d-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="7150d-128">Metoda [GetAvailableThreads –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) Získá počet vláken, která aktuálně nezpracovávají pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="7150d-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="7150d-129">Všechny požadavky nad vrácenou hodnotou parametru `pdwMaxWorkerThreads` zůstanou zařazené do fronty, dokud nebudou vlákna k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7150d-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="7150d-130">Pokud hostitel neposkytuje implementaci `GetMaxThreads`, měla by vrátit hodnotu HRESULT typu E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7150d-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7150d-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7150d-131">Requirements</span></span>  
 <span data-ttu-id="7150d-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7150d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7150d-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7150d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7150d-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7150d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7150d-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7150d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7150d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7150d-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="7150d-137">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="7150d-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="7150d-138">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="7150d-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="7150d-139">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7150d-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
