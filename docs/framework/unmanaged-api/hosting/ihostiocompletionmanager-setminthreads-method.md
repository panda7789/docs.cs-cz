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
ms.openlocfilehash: 5fd37546c63ef5e5f25686e105247555dfeb132a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222780"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="577b2-102">IHostIoCompletionManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="577b2-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="577b2-103">Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="577b2-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="577b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="577b2-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="577b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="577b2-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="577b2-106">[in] Minimální počet vláken dokončení vstupně-výstupních operací, které by měl vytvořit hostitele.</span><span class="sxs-lookup"><span data-stu-id="577b2-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="577b2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="577b2-107">Return Value</span></span>  
  
|<span data-ttu-id="577b2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="577b2-108">HRESULT</span></span>|<span data-ttu-id="577b2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="577b2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="577b2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="577b2-110">S_OK</span></span>|`SetMinThreads` <span data-ttu-id="577b2-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="577b2-111">returned successfully.</span></span>|  
|<span data-ttu-id="577b2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="577b2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="577b2-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="577b2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="577b2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="577b2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="577b2-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="577b2-115">The call timed out.</span></span>|  
|<span data-ttu-id="577b2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="577b2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="577b2-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="577b2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="577b2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="577b2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="577b2-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="577b2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="577b2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="577b2-120">E_FAIL</span></span>|<span data-ttu-id="577b2-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="577b2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="577b2-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="577b2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="577b2-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="577b2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="577b2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="577b2-124">E_NOTIMPL</span></span>|<span data-ttu-id="577b2-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="577b2-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="577b2-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="577b2-126">Remarks</span></span>  
 <span data-ttu-id="577b2-127">Hostitel může být vhodné výhradní kontrolu nad počet vláken, které mohou být přiděleny ke zpracování požadavků na vstupně-výstupních operací, z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="577b2-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="577b2-128">Z tohoto důvodu není potřeba implementovat hostitele `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="577b2-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="577b2-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="577b2-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="577b2-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="577b2-130">Requirements</span></span>  
 <span data-ttu-id="577b2-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="577b2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="577b2-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="577b2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="577b2-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="577b2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="577b2-134">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="577b2-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="577b2-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="577b2-135">See also</span></span>

- [<span data-ttu-id="577b2-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="577b2-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="577b2-137">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="577b2-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="577b2-138">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="577b2-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
