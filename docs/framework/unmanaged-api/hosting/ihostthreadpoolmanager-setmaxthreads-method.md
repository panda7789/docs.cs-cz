---
title: IHostThreadPoolManager::SetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 30c4ff93688396dd9a6a8086fbb53ad1c763ead0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141294"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="8ff6c-102">IHostThreadPoolManager::SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="8ff6c-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="8ff6c-103">Nastaví maximální počet vláken, která může hostitel udržovat ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ff6c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ff6c-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="8ff6c-106">Maximální počet pracovních vláken ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ff6c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8ff6c-107">Return Value</span></span>  
  
|<span data-ttu-id="8ff6c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ff6c-108">HRESULT</span></span>|<span data-ttu-id="8ff6c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8ff6c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ff6c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ff6c-110">S_OK</span></span>|<span data-ttu-id="8ff6c-111">`SetMaxThreads` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8ff6c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ff6c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ff6c-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ff6c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ff6c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ff6c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-115">The call timed out.</span></span>|  
|<span data-ttu-id="8ff6c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ff6c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ff6c-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ff6c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ff6c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ff6c-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ff6c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ff6c-120">E_FAIL</span></span>|<span data-ttu-id="8ff6c-121">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8ff6c-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ff6c-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ff6c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8ff6c-124">E_NOTIMPL</span></span>|<span data-ttu-id="8ff6c-125">Hostitel neposkytuje implementaci `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ff6c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ff6c-126">Remarks</span></span>  
 <span data-ttu-id="8ff6c-127">Hostitel není vyžadován, aby mohl CLR nakonfigurovat velikost fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="8ff6c-128">Někteří hostitelé můžou chtít exkluzivní kontrolu nad fondem vláken, z důvodů, jako je implementace, výkon nebo škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="8ff6c-129">V takovém případě by měl hostitel vracet hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8ff6c-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff6c-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ff6c-130">Requirements</span></span>  
 <span data-ttu-id="8ff6c-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ff6c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff6c-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ff6c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ff6c-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ff6c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ff6c-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff6c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff6c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ff6c-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="8ff6c-136">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="8ff6c-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="8ff6c-137">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="8ff6c-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="8ff6c-138">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ff6c-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
