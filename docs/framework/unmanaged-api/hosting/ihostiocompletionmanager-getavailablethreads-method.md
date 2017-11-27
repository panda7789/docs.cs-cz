---
title: "IHostIoCompletionManager::GetAvailableThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f06e9fe0d07258fca107413d9ad328329b5456b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="d3e84-102">IHostIoCompletionManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d3e84-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="d3e84-103">Získá počet vláken dokončení vstupně-výstupních operací, celkový počet vláken spravuje hostitele, které nejsou aktuálně zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="d3e84-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e84-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3e84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3e84-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="d3e84-106">[out] Ukazatel na počet vstupně-výstupních operací dokončení vláken spravuje hostitele aktuálně dostupné pro žádosti o služby.</span><span class="sxs-lookup"><span data-stu-id="d3e84-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3e84-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d3e84-107">Return Value</span></span>  
  
|<span data-ttu-id="d3e84-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3e84-108">HRESULT</span></span>|<span data-ttu-id="d3e84-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d3e84-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3e84-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3e84-110">S_OK</span></span>|<span data-ttu-id="d3e84-111">`GetAvailableThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d3e84-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d3e84-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3e84-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3e84-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d3e84-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d3e84-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3e84-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d3e84-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d3e84-115">The call timed out.</span></span>|  
|<span data-ttu-id="d3e84-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d3e84-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d3e84-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="d3e84-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d3e84-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d3e84-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d3e84-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="d3e84-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d3e84-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3e84-120">E_FAIL</span></span>|<span data-ttu-id="d3e84-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d3e84-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d3e84-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d3e84-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d3e84-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d3e84-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d3e84-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d3e84-124">E_NOTIMPL</span></span>|<span data-ttu-id="d3e84-125">Hostitel neposkytuje implementace `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="d3e84-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3e84-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3e84-126">Remarks</span></span>  
 <span data-ttu-id="d3e84-127">Hostitel může být vhodné výhradní kontrolu nad velikost fondu vláken dokončení vstupně-výstupních operací, z důvodů, jako je například implementace, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="d3e84-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="d3e84-128">Proto není potřeba hostitele implementovat `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="d3e84-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="d3e84-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="d3e84-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3e84-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3e84-130">Requirements</span></span>  
 <span data-ttu-id="d3e84-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3e84-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3e84-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3e84-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3e84-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3e84-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3e84-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e84-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e84-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3e84-135">See Also</span></span>  
 [<span data-ttu-id="d3e84-136">Iclriocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e84-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="d3e84-137">Ihostiocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e84-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
