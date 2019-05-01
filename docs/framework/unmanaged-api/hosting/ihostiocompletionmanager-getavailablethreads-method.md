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
ms.openlocfilehash: 1e96a12bbf9c4fdc8a0bc79661070eb7fec1a593
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973079"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="1f886-102">IHostIoCompletionManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1f886-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="1f886-103">Získá počet vláken dokončení vstupně-výstupních operací, z celkového počtu vláken spravovaný hostitelem, které momentálně nejsou požadavky obsluhy.</span><span class="sxs-lookup"><span data-stu-id="1f886-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f886-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f886-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f886-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f886-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="1f886-106">[out] Ukazatel na počet vstupně-výstupních operací dokončení vlákna spravováno hostitele, které jsou aktuálně k dispozici žádosti o služby.</span><span class="sxs-lookup"><span data-stu-id="1f886-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f886-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1f886-107">Return Value</span></span>  
  
|<span data-ttu-id="1f886-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f886-108">HRESULT</span></span>|<span data-ttu-id="1f886-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1f886-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f886-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f886-110">S_OK</span></span>|<span data-ttu-id="1f886-111">`GetAvailableThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1f886-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1f886-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f886-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f886-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1f886-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f886-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f886-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f886-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1f886-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f886-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f886-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f886-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="1f886-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f886-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f886-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f886-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="1f886-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f886-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f886-120">E_FAIL</span></span>|<span data-ttu-id="1f886-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1f886-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f886-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1f886-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f886-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f886-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1f886-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1f886-124">E_NOTIMPL</span></span>|<span data-ttu-id="1f886-125">Hostitel neposkytuje implementaci `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="1f886-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f886-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f886-126">Remarks</span></span>  
 <span data-ttu-id="1f886-127">Hostitel může být vhodné výhradní kontrolu nad velikost fondu vláken dokončení vstupně-výstupních operací, z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="1f886-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="1f886-128">Proto není nutné implementovat hostitele `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="1f886-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="1f886-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="1f886-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f886-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f886-130">Requirements</span></span>  
 <span data-ttu-id="1f886-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f886-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f886-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f886-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f886-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f886-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f886-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f886-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f886-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f886-135">See also</span></span>

- [<span data-ttu-id="1f886-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f886-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1f886-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f886-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
