---
title: IHostIoCompletionManager::GetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2022fcbbaaa419048203ecbacfb294160cab5752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779750"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="03711-102">IHostIoCompletionManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="03711-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="03711-103">Získá minimální počet vláken, která hostitel poskytuje pro zpracování požadavků na vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="03711-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03711-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03711-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03711-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03711-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="03711-106">[out] Ukazatel na minimální počet vláken, která obsahuje hostitele na proces vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="03711-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03711-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03711-107">Return Value</span></span>  
  
|<span data-ttu-id="03711-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03711-108">HRESULT</span></span>|<span data-ttu-id="03711-109">Popis</span><span class="sxs-lookup"><span data-stu-id="03711-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03711-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="03711-110">S_OK</span></span>|<span data-ttu-id="03711-111">`GetMinThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="03711-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="03711-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03711-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03711-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="03711-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03711-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03711-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03711-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="03711-115">The call timed out.</span></span>|  
|<span data-ttu-id="03711-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03711-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03711-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="03711-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03711-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03711-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03711-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="03711-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03711-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03711-120">E_FAIL</span></span>|<span data-ttu-id="03711-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="03711-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03711-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="03711-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03711-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="03711-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="03711-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="03711-124">E_NOTIMPL</span></span>|<span data-ttu-id="03711-125">Hostitel neposkytuje implementaci `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="03711-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03711-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03711-126">Remarks</span></span>  
 <span data-ttu-id="03711-127">Výhradní kontrolu nad počet vláken přidělený žádosti o vstupně-výstupní operace služby, například provádění, výkon a škálovatelnost z důvodů může být vhodné hostitele.</span><span class="sxs-lookup"><span data-stu-id="03711-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="03711-128">Z tohoto důvodu není potřeba implementovat hostitele `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="03711-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="03711-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="03711-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03711-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03711-130">Requirements</span></span>  
 <span data-ttu-id="03711-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03711-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03711-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03711-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03711-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03711-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03711-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03711-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03711-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03711-135">See also</span></span>

- [<span data-ttu-id="03711-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03711-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="03711-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03711-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
