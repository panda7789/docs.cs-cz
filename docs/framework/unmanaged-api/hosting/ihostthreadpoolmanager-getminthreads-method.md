---
title: IHostThreadPoolManager::GetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: ce1abb75c5135a9bb23f1ad2d2acbd40d9111b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122070"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="b1c02-102">IHostThreadPoolManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b1c02-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="b1c02-103">Získá minimální počet nečinných vláken, která hostitel udržuje ve fondu vláken při předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="b1c02-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1c02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1c02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1c02-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="b1c02-106">mimo Ukazatel na minimální počet nečinných pracovních vláken, které aktuálně udržuje hostitel.</span><span class="sxs-lookup"><span data-stu-id="b1c02-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1c02-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1c02-107">Return Value</span></span>  
  
|<span data-ttu-id="b1c02-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1c02-108">HRESULT</span></span>|<span data-ttu-id="b1c02-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b1c02-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1c02-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1c02-110">S_OK</span></span>|<span data-ttu-id="b1c02-111">`GetMinThreads` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b1c02-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b1c02-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1c02-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1c02-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b1c02-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1c02-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1c02-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1c02-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b1c02-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1c02-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1c02-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1c02-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b1c02-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1c02-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1c02-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1c02-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b1c02-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1c02-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1c02-120">E_FAIL</span></span>|<span data-ttu-id="b1c02-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b1c02-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1c02-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b1c02-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1c02-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1c02-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1c02-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b1c02-124">E_NOTIMPL</span></span>|<span data-ttu-id="b1c02-125">Hostitel neposkytuje implementaci `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="b1c02-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1c02-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1c02-126">Remarks</span></span>  
 <span data-ttu-id="b1c02-127">Hostitel není vyžadován k poskytování implementace `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="b1c02-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="b1c02-128">V takovém případě by měla vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b1c02-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c02-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1c02-129">Requirements</span></span>  
 <span data-ttu-id="b1c02-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c02-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c02-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1c02-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1c02-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1c02-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1c02-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c02-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c02-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1c02-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b1c02-135">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b1c02-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="b1c02-136">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b1c02-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="b1c02-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1c02-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
