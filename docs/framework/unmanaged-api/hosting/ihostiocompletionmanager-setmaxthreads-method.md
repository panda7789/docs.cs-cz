---
title: IHostIoCompletionManager::SetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 345c7b88b6967773a185538943591383a686748c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224063"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="3df00-102">IHostIoCompletionManager::SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="3df00-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="3df00-103">Nastaví maximální počet vláken, která allots hostitele služby vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="3df00-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3df00-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3df00-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="3df00-106">[in] Maximální počet vláken, chcete-li přidělit pro vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="3df00-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3df00-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3df00-107">Return Value</span></span>  
  
|<span data-ttu-id="3df00-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3df00-108">HRESULT</span></span>|<span data-ttu-id="3df00-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3df00-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3df00-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3df00-110">S_OK</span></span>|`SetMaxThreads` <span data-ttu-id="3df00-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="3df00-111">returned successfully.</span></span>|  
|<span data-ttu-id="3df00-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3df00-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3df00-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3df00-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3df00-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3df00-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3df00-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3df00-115">The call timed out.</span></span>|  
|<span data-ttu-id="3df00-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3df00-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3df00-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="3df00-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3df00-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3df00-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3df00-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="3df00-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3df00-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3df00-120">E_FAIL</span></span>|<span data-ttu-id="3df00-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="3df00-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3df00-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3df00-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3df00-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3df00-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3df00-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3df00-124">E_NOTIMPL</span></span>|<span data-ttu-id="3df00-125">Hostitel neposkytuje implementaci `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="3df00-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3df00-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3df00-126">Remarks</span></span>  
 `SetMaxThreads` <span data-ttu-id="3df00-127">CLR poskytuje možnost nastavit maximální počet vláken, které jsou k dispozici pro žádosti o službu na portech vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="3df00-127">provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="3df00-128">Hostitel může být nutné výhradní kontrolu nad velikost fondu vláken z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="3df00-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3df00-129">Z tohoto důvodu není potřeba implementovat hostitele `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="3df00-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="3df00-130">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="3df00-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df00-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3df00-131">Requirements</span></span>  
 <span data-ttu-id="3df00-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df00-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df00-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3df00-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3df00-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3df00-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3df00-135">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3df00-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3df00-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3df00-136">See also</span></span>

- [<span data-ttu-id="3df00-137">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3df00-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3df00-138">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3df00-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
