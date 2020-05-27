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
ms.openlocfilehash: a05cfb43b5b4a328d22c4df04049a7fa156ca080
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841929"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="6bbea-102">IHostThreadPoolManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="6bbea-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="6bbea-103">Získá minimální počet nečinných vláken, která hostitel udržuje ve fondu vláken při předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="6bbea-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bbea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bbea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bbea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bbea-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="6bbea-106">mimo Ukazatel na minimální počet nečinných pracovních vláken, které aktuálně udržuje hostitel.</span><span class="sxs-lookup"><span data-stu-id="6bbea-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bbea-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bbea-107">Return Value</span></span>  
  
|<span data-ttu-id="6bbea-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bbea-108">HRESULT</span></span>|<span data-ttu-id="6bbea-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6bbea-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6bbea-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6bbea-110">S_OK</span></span>|<span data-ttu-id="6bbea-111">`GetMinThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6bbea-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="6bbea-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6bbea-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6bbea-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6bbea-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6bbea-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6bbea-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6bbea-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6bbea-115">The call timed out.</span></span>|  
|<span data-ttu-id="6bbea-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6bbea-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6bbea-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6bbea-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6bbea-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6bbea-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6bbea-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6bbea-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6bbea-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6bbea-120">E_FAIL</span></span>|<span data-ttu-id="6bbea-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6bbea-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6bbea-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6bbea-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6bbea-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6bbea-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6bbea-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="6bbea-124">E_NOTIMPL</span></span>|<span data-ttu-id="6bbea-125">Hostitel neposkytuje implementaci `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="6bbea-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bbea-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bbea-126">Remarks</span></span>  
 <span data-ttu-id="6bbea-127">Hostitel není vyžadován k poskytnutí implementace `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="6bbea-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="6bbea-128">V takovém případě by měla vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="6bbea-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bbea-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bbea-129">Requirements</span></span>  
 <span data-ttu-id="6bbea-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bbea-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bbea-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6bbea-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bbea-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6bbea-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bbea-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bbea-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbea-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bbea-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="6bbea-135">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="6bbea-135">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="6bbea-136">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="6bbea-136">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="6bbea-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bbea-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
