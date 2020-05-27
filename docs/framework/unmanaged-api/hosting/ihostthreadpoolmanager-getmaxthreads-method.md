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
ms.openlocfilehash: efbfa310c90f48c99219cb185f090a1b854949a2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842280"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="34e3e-102">IHostThreadPoolManager::GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="34e3e-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="34e3e-103">Získá maximální počet vláken, která hostitel udržuje souběžně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="34e3e-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34e3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34e3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34e3e-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="34e3e-106">mimo Ukazatel na maximální počet vláken, která hostitel udržuje ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="34e3e-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34e3e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="34e3e-107">Return Value</span></span>  
  
|<span data-ttu-id="34e3e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34e3e-108">HRESULT</span></span>|<span data-ttu-id="34e3e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="34e3e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34e3e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34e3e-110">S_OK</span></span>|<span data-ttu-id="34e3e-111">`GetMaxThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="34e3e-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="34e3e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34e3e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34e3e-113">Modul CLR (Common Language Runtime) (CLR (nebyl načten do procesu) nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="34e3e-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34e3e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34e3e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34e3e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="34e3e-115">The call timed out.</span></span>|  
|<span data-ttu-id="34e3e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34e3e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34e3e-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="34e3e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34e3e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34e3e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34e3e-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="34e3e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34e3e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34e3e-120">E_FAIL</span></span>|<span data-ttu-id="34e3e-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="34e3e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34e3e-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="34e3e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34e3e-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34e3e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="34e3e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="34e3e-124">E_NOTIMPL</span></span>|<span data-ttu-id="34e3e-125">Hostitel neposkytuje implementaci `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="34e3e-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e3e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34e3e-126">Remarks</span></span>  
 <span data-ttu-id="34e3e-127">Modul CLR volá `GetMaxThreads` k určení celkového počtu vláken ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="34e3e-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="34e3e-128">Metoda [GetAvailableThreads –](ihostthreadpoolmanager-getavailablethreads-method.md) Získá počet vláken, která aktuálně nezpracovávají pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="34e3e-128">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="34e3e-129">Všechny žádosti nad vrácenou hodnotou `pdwMaxWorkerThreads` parametru zůstanou zařazené do fronty, dokud nebudou vlákna k dispozici.</span><span class="sxs-lookup"><span data-stu-id="34e3e-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="34e3e-130">Pokud hostitel neposkytuje implementaci `GetMaxThreads` , měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="34e3e-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34e3e-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34e3e-131">Requirements</span></span>  
 <span data-ttu-id="34e3e-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e3e-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34e3e-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34e3e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34e3e-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="34e3e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34e3e-135">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34e3e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e3e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="34e3e-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="34e3e-137">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="34e3e-137">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="34e3e-138">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="34e3e-138">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="34e3e-139">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34e3e-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
