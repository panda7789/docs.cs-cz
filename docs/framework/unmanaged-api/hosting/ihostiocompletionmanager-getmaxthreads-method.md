---
title: IHostIoCompletionManager::GetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fcd66914448fa63c892f7285b8cd364d4cacc5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779218"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="d62e7-102">IHostIoCompletionManager::GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d62e7-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="d62e7-103">Získá maximální počet vláken, která může přidělit hostitele služby vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="d62e7-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d62e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d62e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d62e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d62e7-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="d62e7-106">[out] Ukazatel na maximální počet vláken ve fondu vláken, které hostitele může přidělit na vstupně-výstupní operace žádosti o služby.</span><span class="sxs-lookup"><span data-stu-id="d62e7-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d62e7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d62e7-107">Return Value</span></span>  
  
|<span data-ttu-id="d62e7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d62e7-108">HRESULT</span></span>|<span data-ttu-id="d62e7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d62e7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d62e7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d62e7-110">S_OK</span></span>|<span data-ttu-id="d62e7-111">`GetMaxThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d62e7-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d62e7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d62e7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d62e7-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d62e7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d62e7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d62e7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d62e7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d62e7-115">The call timed out.</span></span>|  
|<span data-ttu-id="d62e7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d62e7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d62e7-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d62e7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d62e7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d62e7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d62e7-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d62e7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d62e7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d62e7-120">E_FAIL</span></span>|<span data-ttu-id="d62e7-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d62e7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d62e7-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d62e7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d62e7-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d62e7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d62e7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d62e7-124">E_NOTIMPL</span></span>|<span data-ttu-id="d62e7-125">Hostitel neposkytuje implementaci `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="d62e7-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d62e7-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d62e7-126">Remarks</span></span>  
 <span data-ttu-id="d62e7-127">Hostitel může být vhodné výhradní kontrolu nad počet vláken, které mohou být přiděleny ke zpracování požadavků na vstupně-výstupních operací, z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="d62e7-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="d62e7-128">Z tohoto důvodu není potřeba implementovat hostitele `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="d62e7-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="d62e7-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="d62e7-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d62e7-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d62e7-130">Requirements</span></span>  
 <span data-ttu-id="d62e7-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d62e7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d62e7-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d62e7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d62e7-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d62e7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d62e7-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d62e7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62e7-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d62e7-135">See also</span></span>

- [<span data-ttu-id="d62e7-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d62e7-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="d62e7-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d62e7-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
