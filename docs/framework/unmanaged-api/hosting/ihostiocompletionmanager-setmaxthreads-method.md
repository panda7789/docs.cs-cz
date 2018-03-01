---
title: "IHostIoCompletionManager::SetMaxThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3d2d8436d85f7be40c89693628794b007e0c6a88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="ef261-102">IHostIoCompletionManager::SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="ef261-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="ef261-103">Nastaví maximální počet vláken, která allots hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="ef261-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef261-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef261-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef261-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef261-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="ef261-106">[v] Maximální počet vláken, chcete-li přidělit pro vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="ef261-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef261-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ef261-107">Return Value</span></span>  
  
|<span data-ttu-id="ef261-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef261-108">HRESULT</span></span>|<span data-ttu-id="ef261-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ef261-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef261-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef261-110">S_OK</span></span>|<span data-ttu-id="ef261-111">`SetMaxThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ef261-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="ef261-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef261-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef261-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ef261-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef261-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef261-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef261-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ef261-115">The call timed out.</span></span>|  
|<span data-ttu-id="ef261-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef261-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef261-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ef261-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef261-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef261-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef261-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ef261-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef261-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef261-120">E_FAIL</span></span>|<span data-ttu-id="ef261-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ef261-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef261-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ef261-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef261-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef261-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ef261-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ef261-124">E_NOTIMPL</span></span>|<span data-ttu-id="ef261-125">Hostitel neposkytuje implementace `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="ef261-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef261-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef261-126">Remarks</span></span>  
 <span data-ttu-id="ef261-127">`SetMaxThreads`poskytuje možnost nastavit maximální počet vláken, které jsou k dispozici pro žádosti o službu na portech vstupně-výstupních operací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ef261-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="ef261-128">Hostitel může být nutné výhradní kontrolu nad velikost fondu vláken z důvodů, jako je například implementace, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ef261-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="ef261-129">Z tohoto důvodu není potřeba implementovat hostitele `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="ef261-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="ef261-130">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="ef261-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef261-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef261-131">Requirements</span></span>  
 <span data-ttu-id="ef261-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef261-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef261-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef261-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef261-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef261-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef261-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef261-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef261-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef261-136">See Also</span></span>  
 [<span data-ttu-id="ef261-137">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef261-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="ef261-138">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef261-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
