---
title: IHostThreadPoolManager::SetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: f2d2665382559596563d9b155d2afa4d99c91ee7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141255"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="9950c-102">IHostThreadPoolManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="9950c-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="9950c-103">Nastaví minimální počet nečinných vláken, které musí hostitel uchovávat při předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="9950c-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9950c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9950c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9950c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9950c-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="9950c-106">pro Nový minimální počet vláken, která musí hostitel udržovat.</span><span class="sxs-lookup"><span data-stu-id="9950c-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9950c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9950c-107">Return Value</span></span>  
  
|<span data-ttu-id="9950c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9950c-108">HRESULT</span></span>|<span data-ttu-id="9950c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9950c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9950c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9950c-110">S_OK</span></span>|<span data-ttu-id="9950c-111">`SetMinThreads` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9950c-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9950c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9950c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9950c-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9950c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9950c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9950c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9950c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9950c-115">The call timed out.</span></span>|  
|<span data-ttu-id="9950c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9950c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9950c-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9950c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9950c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9950c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9950c-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9950c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9950c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9950c-120">E_FAIL</span></span>|<span data-ttu-id="9950c-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9950c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9950c-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9950c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9950c-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9950c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9950c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9950c-124">E_NOTIMPL</span></span>|<span data-ttu-id="9950c-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="9950c-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9950c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9950c-126">Remarks</span></span>  
 <span data-ttu-id="9950c-127">Hostitel není vyžadován k poskytování implementace `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="9950c-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="9950c-128">V takovém případě by měla vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="9950c-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9950c-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9950c-129">Requirements</span></span>  
 <span data-ttu-id="9950c-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9950c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9950c-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9950c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9950c-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9950c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9950c-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9950c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9950c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9950c-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="9950c-135">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="9950c-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="9950c-136">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="9950c-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="9950c-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9950c-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
