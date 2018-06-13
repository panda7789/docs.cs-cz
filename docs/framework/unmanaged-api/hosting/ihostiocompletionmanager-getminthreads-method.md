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
ms.openlocfilehash: 353d98feed2ab54cf13af92883348598e822c1d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439088"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="da9d6-102">IHostIoCompletionManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="da9d6-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="da9d6-103">Získá minimální počet vláken, které hostitel poskytuje pro zpracování požadavků vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="da9d6-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da9d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da9d6-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da9d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da9d6-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="da9d6-106">[out] Ukazatel na minimální počet vláken, která hostitel poskytuje k procesu vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="da9d6-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da9d6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da9d6-107">Return Value</span></span>  
  
|<span data-ttu-id="da9d6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da9d6-108">HRESULT</span></span>|<span data-ttu-id="da9d6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="da9d6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da9d6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="da9d6-110">S_OK</span></span>|<span data-ttu-id="da9d6-111">`GetMinThreads` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="da9d6-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="da9d6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da9d6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da9d6-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="da9d6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da9d6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da9d6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da9d6-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="da9d6-115">The call timed out.</span></span>|  
|<span data-ttu-id="da9d6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da9d6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da9d6-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="da9d6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da9d6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da9d6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da9d6-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="da9d6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da9d6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da9d6-120">E_FAIL</span></span>|<span data-ttu-id="da9d6-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="da9d6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da9d6-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="da9d6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da9d6-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="da9d6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="da9d6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="da9d6-124">E_NOTIMPL</span></span>|<span data-ttu-id="da9d6-125">Hostitel neposkytuje implementace `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="da9d6-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da9d6-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da9d6-126">Remarks</span></span>  
 <span data-ttu-id="da9d6-127">Hostitel může být vhodné výhradní kontrolu nad počet vláken vymezena pro žádosti o vstupně-výstupní operace služby, z důvodů, jako je například implementace, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="da9d6-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="da9d6-128">Z tohoto důvodu není potřeba implementovat hostitele `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="da9d6-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="da9d6-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="da9d6-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da9d6-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da9d6-130">Requirements</span></span>  
 <span data-ttu-id="da9d6-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da9d6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da9d6-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da9d6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da9d6-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da9d6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da9d6-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da9d6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9d6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="da9d6-135">See Also</span></span>  
 [<span data-ttu-id="da9d6-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da9d6-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="da9d6-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da9d6-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
