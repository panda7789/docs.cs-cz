---
title: IHostIoCompletionManager::GetAvailableThreads – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ef25267f6af5d1f8503825e2784383a0eb241e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535529"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="83499-102">IHostIoCompletionManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="83499-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="83499-103">Získá počet vláken dokončení vstupně-výstupních operací, z celkového počtu vláken spravovaný hostitelem, které momentálně nejsou požadavky obsluhy.</span><span class="sxs-lookup"><span data-stu-id="83499-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83499-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83499-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83499-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83499-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="83499-106">[out] Ukazatel na počet vstupně-výstupních operací dokončení vlákna spravováno hostitele, které jsou aktuálně k dispozici žádosti o služby.</span><span class="sxs-lookup"><span data-stu-id="83499-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83499-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83499-107">Return Value</span></span>  
  
|<span data-ttu-id="83499-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83499-108">HRESULT</span></span>|<span data-ttu-id="83499-109">Popis</span><span class="sxs-lookup"><span data-stu-id="83499-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83499-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83499-110">S_OK</span></span>|<span data-ttu-id="83499-111">`GetAvailableThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="83499-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="83499-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83499-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83499-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="83499-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83499-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83499-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83499-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="83499-115">The call timed out.</span></span>|  
|<span data-ttu-id="83499-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83499-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83499-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="83499-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83499-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83499-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83499-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="83499-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83499-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83499-120">E_FAIL</span></span>|<span data-ttu-id="83499-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="83499-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83499-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="83499-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83499-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83499-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="83499-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="83499-124">E_NOTIMPL</span></span>|<span data-ttu-id="83499-125">Hostitel neposkytuje implementaci `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="83499-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83499-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83499-126">Remarks</span></span>  
 <span data-ttu-id="83499-127">Hostitel může být vhodné výhradní kontrolu nad velikost fondu vláken dokončení vstupně-výstupních operací, z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="83499-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="83499-128">Proto není nutné implementovat hostitele `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="83499-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="83499-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="83499-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83499-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83499-130">Requirements</span></span>  
 <span data-ttu-id="83499-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83499-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83499-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83499-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83499-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83499-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83499-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83499-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83499-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83499-135">See also</span></span>
- [<span data-ttu-id="83499-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83499-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="83499-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83499-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
