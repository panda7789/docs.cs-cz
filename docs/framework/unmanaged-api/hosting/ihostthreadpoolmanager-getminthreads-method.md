---
title: "IHostThreadPoolManager::GetMinThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8ee8adfb93a3e098bb6df69ad00202118bc1731e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="5e76a-102">IHostThreadPoolManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="5e76a-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="5e76a-103">Získá minimální počet nečinných vláken, která udržuje hostitele ve fondu vláken v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="5e76a-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e76a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e76a-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e76a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e76a-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="5e76a-106">[out] Ukazatel na minimální počet nečinnosti pracovních vláken, které aktuálně udržuje hostitele.</span><span class="sxs-lookup"><span data-stu-id="5e76a-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e76a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5e76a-107">Return Value</span></span>  
  
|<span data-ttu-id="5e76a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e76a-108">HRESULT</span></span>|<span data-ttu-id="5e76a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5e76a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e76a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e76a-110">S_OK</span></span>|<span data-ttu-id="5e76a-111">`GetMinThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5e76a-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5e76a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e76a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e76a-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5e76a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e76a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e76a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e76a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5e76a-115">The call timed out.</span></span>|  
|<span data-ttu-id="5e76a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e76a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e76a-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="5e76a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e76a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e76a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e76a-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="5e76a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e76a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e76a-120">E_FAIL</span></span>|<span data-ttu-id="5e76a-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="5e76a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e76a-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5e76a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e76a-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5e76a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e76a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5e76a-124">E_NOTIMPL</span></span>|<span data-ttu-id="5e76a-125">Hostitel neposkytuje implementace `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5e76a-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e76a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e76a-126">Remarks</span></span>  
 <span data-ttu-id="5e76a-127">Hostitel není potřeba poskytnout implementaci `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5e76a-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="5e76a-128">V takovém případě má být vrácen při použití hodnoty HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5e76a-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e76a-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e76a-129">Requirements</span></span>  
 <span data-ttu-id="5e76a-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e76a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e76a-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e76a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e76a-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e76a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e76a-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e76a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e76a-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e76a-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="5e76a-135">Getmaxthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="5e76a-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="5e76a-136">Setminthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="5e76a-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="5e76a-137">Ihostthreadpoolmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e76a-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
