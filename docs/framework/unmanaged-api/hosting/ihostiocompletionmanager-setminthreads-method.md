---
title: IHostIoCompletionManager::SetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 8b1fc936b601d327ce6306f22dbec2c1078718da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133737"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="95023-102">IHostIoCompletionManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="95023-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="95023-103">Nastaví minimální počet vláken, které by měl hostitel Allot na dokončení vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="95023-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95023-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95023-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95023-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95023-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="95023-106">pro Minimální počet vláken dokončování v/v, které by měl hostitel vytvořit.</span><span class="sxs-lookup"><span data-stu-id="95023-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95023-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95023-107">Return Value</span></span>  
  
|<span data-ttu-id="95023-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95023-108">HRESULT</span></span>|<span data-ttu-id="95023-109">Popis</span><span class="sxs-lookup"><span data-stu-id="95023-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95023-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="95023-110">S_OK</span></span>|<span data-ttu-id="95023-111">`SetMinThreads` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="95023-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="95023-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95023-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95023-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="95023-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95023-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95023-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95023-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="95023-115">The call timed out.</span></span>|  
|<span data-ttu-id="95023-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95023-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95023-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="95023-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95023-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95023-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95023-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="95023-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95023-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95023-120">E_FAIL</span></span>|<span data-ttu-id="95023-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="95023-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95023-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="95023-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95023-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95023-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95023-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="95023-124">E_NOTIMPL</span></span>|<span data-ttu-id="95023-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="95023-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95023-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95023-126">Remarks</span></span>  
 <span data-ttu-id="95023-127">Hostitel může chtít exkluzivní kontrolu nad počtem vláken, která je možné přiděluje zpracování vstupně-výstupních požadavků, z důvodů, jako je implementace, výkon nebo škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="95023-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="95023-128">Z tohoto důvodu není nutné, aby hostitel implementoval `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="95023-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="95023-129">V takovém případě by měl hostitel vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="95023-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95023-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95023-130">Requirements</span></span>  
 <span data-ttu-id="95023-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95023-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95023-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="95023-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95023-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95023-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95023-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95023-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95023-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95023-135">See also</span></span>

- [<span data-ttu-id="95023-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95023-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="95023-137">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="95023-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="95023-138">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95023-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
