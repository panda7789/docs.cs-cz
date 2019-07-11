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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55570050a4053eac6327f9d7887c2fcd08eceab7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780740"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="dcdf9-102">IHostIoCompletionManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="dcdf9-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="dcdf9-103">Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdf9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcdf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcdf9-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="dcdf9-106">[in] Minimální počet vláken dokončení vstupně-výstupních operací, které by měl vytvořit hostitele.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcdf9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dcdf9-107">Return Value</span></span>  
  
|<span data-ttu-id="dcdf9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcdf9-108">HRESULT</span></span>|<span data-ttu-id="dcdf9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dcdf9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcdf9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcdf9-110">S_OK</span></span>|<span data-ttu-id="dcdf9-111">`SetMinThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="dcdf9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcdf9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcdf9-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcdf9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcdf9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcdf9-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-115">The call timed out.</span></span>|  
|<span data-ttu-id="dcdf9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcdf9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcdf9-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcdf9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcdf9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcdf9-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcdf9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcdf9-120">E_FAIL</span></span>|<span data-ttu-id="dcdf9-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcdf9-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcdf9-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dcdf9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="dcdf9-124">E_NOTIMPL</span></span>|<span data-ttu-id="dcdf9-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcdf9-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcdf9-126">Remarks</span></span>  
 <span data-ttu-id="dcdf9-127">Hostitel může být vhodné výhradní kontrolu nad počet vláken, které mohou být přiděleny ke zpracování požadavků na vstupně-výstupních operací, z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="dcdf9-128">Z tohoto důvodu není potřeba implementovat hostitele `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="dcdf9-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="dcdf9-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcdf9-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcdf9-130">Requirements</span></span>  
 <span data-ttu-id="dcdf9-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdf9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdf9-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcdf9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcdf9-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcdf9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcdf9-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdf9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdf9-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcdf9-135">See also</span></span>

- [<span data-ttu-id="dcdf9-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdf9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="dcdf9-137">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="dcdf9-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="dcdf9-138">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdf9-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
