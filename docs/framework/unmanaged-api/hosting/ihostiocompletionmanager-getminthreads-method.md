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
ms.openlocfilehash: f0ba01b576903d08139cfa57c285d079ea692c78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614468"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="9893f-102">IHostIoCompletionManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="9893f-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="9893f-103">Získá minimální počet vláken, která hostitel poskytuje pro zpracování požadavků na vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="9893f-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9893f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9893f-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9893f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9893f-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="9893f-106">[out] Ukazatel na minimální počet vláken, která obsahuje hostitele na proces vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="9893f-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9893f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9893f-107">Return Value</span></span>  
  
|<span data-ttu-id="9893f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9893f-108">HRESULT</span></span>|<span data-ttu-id="9893f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9893f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9893f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9893f-110">S_OK</span></span>|<span data-ttu-id="9893f-111">`GetMinThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="9893f-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9893f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9893f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9893f-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9893f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9893f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9893f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9893f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9893f-115">The call timed out.</span></span>|  
|<span data-ttu-id="9893f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9893f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9893f-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="9893f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9893f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9893f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9893f-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="9893f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9893f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9893f-120">E_FAIL</span></span>|<span data-ttu-id="9893f-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="9893f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9893f-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9893f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9893f-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9893f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9893f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9893f-124">E_NOTIMPL</span></span>|<span data-ttu-id="9893f-125">Hostitel neposkytuje implementaci `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="9893f-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9893f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9893f-126">Remarks</span></span>  
 <span data-ttu-id="9893f-127">Výhradní kontrolu nad počet vláken přidělený žádosti o vstupně-výstupní operace služby, například provádění, výkon a škálovatelnost z důvodů může být vhodné hostitele.</span><span class="sxs-lookup"><span data-stu-id="9893f-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9893f-128">Z tohoto důvodu není potřeba implementovat hostitele `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="9893f-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="9893f-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="9893f-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9893f-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9893f-130">Requirements</span></span>  
 <span data-ttu-id="9893f-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9893f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9893f-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9893f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9893f-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9893f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9893f-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9893f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9893f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9893f-135">See also</span></span>
- [<span data-ttu-id="9893f-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9893f-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="9893f-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9893f-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
