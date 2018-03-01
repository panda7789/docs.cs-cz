---
title: "IHostIoCompletionManager::GetMaxThreads – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d02b0ba4802b72932ea6d23c66153c265a3d6498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="11d38-102">IHostIoCompletionManager::GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="11d38-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="11d38-103">Získá maximální počet vláken, které můžete přidělit hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="11d38-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d38-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11d38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11d38-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="11d38-106">[out] Ukazatel na maximální počet vláken ve fondu vláken, který se žádostí o službu vstupně-výstupních operací můžete přidělit hostitele.</span><span class="sxs-lookup"><span data-stu-id="11d38-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11d38-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="11d38-107">Return Value</span></span>  
  
|<span data-ttu-id="11d38-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11d38-108">HRESULT</span></span>|<span data-ttu-id="11d38-109">Popis</span><span class="sxs-lookup"><span data-stu-id="11d38-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11d38-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11d38-110">S_OK</span></span>|<span data-ttu-id="11d38-111">`GetMaxThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="11d38-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="11d38-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11d38-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11d38-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="11d38-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11d38-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11d38-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11d38-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="11d38-115">The call timed out.</span></span>|  
|<span data-ttu-id="11d38-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11d38-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11d38-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="11d38-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11d38-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11d38-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11d38-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="11d38-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11d38-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11d38-120">E_FAIL</span></span>|<span data-ttu-id="11d38-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="11d38-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11d38-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="11d38-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11d38-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11d38-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11d38-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="11d38-124">E_NOTIMPL</span></span>|<span data-ttu-id="11d38-125">Hostitel neposkytuje implementace `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="11d38-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11d38-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11d38-126">Remarks</span></span>  
 <span data-ttu-id="11d38-127">Hostitel může být vhodné výhradní kontrolu nad počet vláken, které můžou být přiděleny zpracovávat požadavky na vstupně-výstupních operací, z důvodů, jako je například implementace, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="11d38-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="11d38-128">Z tohoto důvodu není potřeba implementovat hostitele `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="11d38-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="11d38-129">V takovém případě hostitele by měl vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="11d38-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d38-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11d38-130">Requirements</span></span>  
 <span data-ttu-id="11d38-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11d38-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d38-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11d38-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11d38-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11d38-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11d38-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11d38-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d38-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d38-135">See Also</span></span>  
 [<span data-ttu-id="11d38-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d38-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="11d38-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d38-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
