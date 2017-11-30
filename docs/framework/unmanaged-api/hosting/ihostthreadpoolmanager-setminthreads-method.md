---
title: "IHostThreadPoolManager::SetMinThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab0b107c050b1c4b686f761ede75ea2349825270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="2edc4-102">IHostThreadPoolManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="2edc4-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="2edc4-103">Nastaví minimální počet nečinných vláken, která musí zachovat hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="2edc4-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2edc4-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2edc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2edc4-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="2edc4-106">[v] Nové minimální počet vláken, která musí zachovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="2edc4-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2edc4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2edc4-107">Return Value</span></span>  
  
|<span data-ttu-id="2edc4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2edc4-108">HRESULT</span></span>|<span data-ttu-id="2edc4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2edc4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2edc4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2edc4-110">S_OK</span></span>|<span data-ttu-id="2edc4-111">`SetMinThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2edc4-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2edc4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2edc4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2edc4-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2edc4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2edc4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2edc4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2edc4-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2edc4-115">The call timed out.</span></span>|  
|<span data-ttu-id="2edc4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2edc4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2edc4-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="2edc4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2edc4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2edc4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2edc4-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="2edc4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2edc4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2edc4-120">E_FAIL</span></span>|<span data-ttu-id="2edc4-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="2edc4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2edc4-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2edc4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2edc4-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2edc4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2edc4-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2edc4-124">E_NOTIMPL</span></span>|<span data-ttu-id="2edc4-125">Hostitel neposkytuje implementace `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="2edc4-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2edc4-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2edc4-126">Remarks</span></span>  
 <span data-ttu-id="2edc4-127">Hostitel není potřeba poskytnout implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="2edc4-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="2edc4-128">V takovém případě má být vrácen při použití hodnoty HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2edc4-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2edc4-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2edc4-129">Requirements</span></span>  
 <span data-ttu-id="2edc4-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2edc4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2edc4-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2edc4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2edc4-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2edc4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2edc4-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2edc4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edc4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2edc4-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="2edc4-135">Getminthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="2edc4-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="2edc4-136">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="2edc4-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="2edc4-137">Ihostthreadpoolmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2edc4-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
