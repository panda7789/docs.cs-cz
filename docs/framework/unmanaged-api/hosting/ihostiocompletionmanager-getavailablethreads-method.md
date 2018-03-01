---
title: "IHostIoCompletionManager::GetAvailableThreads – metoda"
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
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66f2471e07ae5827d2edb553b4226784b42278c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="c4a82-102">IHostIoCompletionManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c4a82-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="c4a82-103">Získá počet vláken dokončení vstupně-výstupních operací, celkový počet vláken spravuje hostitele, které nejsou aktuálně zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="c4a82-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a82-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4a82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4a82-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="c4a82-106">[out] Ukazatel na počet vstupně-výstupních operací dokončení vláken spravuje hostitele aktuálně dostupné pro žádosti o služby.</span><span class="sxs-lookup"><span data-stu-id="c4a82-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4a82-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4a82-107">Return Value</span></span>  
  
|<span data-ttu-id="c4a82-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4a82-108">HRESULT</span></span>|<span data-ttu-id="c4a82-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c4a82-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4a82-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4a82-110">S_OK</span></span>|<span data-ttu-id="c4a82-111">`GetAvailableThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c4a82-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="c4a82-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4a82-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4a82-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c4a82-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4a82-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4a82-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4a82-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c4a82-115">The call timed out.</span></span>|  
|<span data-ttu-id="c4a82-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4a82-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4a82-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c4a82-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4a82-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4a82-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4a82-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c4a82-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4a82-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4a82-120">E_FAIL</span></span>|<span data-ttu-id="c4a82-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c4a82-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4a82-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c4a82-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4a82-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4a82-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c4a82-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c4a82-124">E_NOTIMPL</span></span>|<span data-ttu-id="c4a82-125">Hostitel neposkytuje implementace `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="c4a82-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4a82-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4a82-126">Remarks</span></span>  
 <span data-ttu-id="c4a82-127">Hostitel může být vhodné výhradní kontrolu nad velikost fondu vláken dokončení vstupně-výstupních operací, z důvodů, jako je například implementace, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="c4a82-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="c4a82-128">Proto není potřeba hostitele implementovat `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="c4a82-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="c4a82-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="c4a82-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a82-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4a82-130">Requirements</span></span>  
 <span data-ttu-id="c4a82-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4a82-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a82-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4a82-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4a82-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4a82-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4a82-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a82-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a82-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4a82-135">See Also</span></span>  
 [<span data-ttu-id="c4a82-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4a82-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c4a82-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4a82-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
