---
title: "IHostThreadPoolManager::GetAvailableThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5151b26bad08ef8e1e3c53d649f57f79eb18d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="4bca1-102">IHostThreadPoolManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="4bca1-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="4bca1-103">Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="4bca1-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bca1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bca1-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bca1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bca1-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="4bca1-106">[out] Ukazatel na počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="4bca1-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bca1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4bca1-107">Return Value</span></span>  
  
|<span data-ttu-id="4bca1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bca1-108">HRESULT</span></span>|<span data-ttu-id="4bca1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4bca1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bca1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bca1-110">S_OK</span></span>|<span data-ttu-id="4bca1-111">`GetAvailableThreads`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4bca1-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4bca1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bca1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bca1-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4bca1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bca1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bca1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bca1-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4bca1-115">The call timed out.</span></span>|  
|<span data-ttu-id="4bca1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bca1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bca1-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="4bca1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bca1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bca1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bca1-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="4bca1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bca1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bca1-120">E_FAIL</span></span>|<span data-ttu-id="4bca1-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="4bca1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bca1-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4bca1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bca1-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4bca1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bca1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4bca1-124">E_NOTIMPL</span></span>|<span data-ttu-id="4bca1-125">Hostitel neposkytuje implementace `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="4bca1-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bca1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bca1-126">Remarks</span></span>  
 <span data-ttu-id="4bca1-127">Pokud hostitel neposkytne implementace `GetAvailableThreads`, má hodnotu HRESULT E_NOTIMPL má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="4bca1-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bca1-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bca1-128">Requirements</span></span>  
 <span data-ttu-id="4bca1-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bca1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bca1-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bca1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bca1-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4bca1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bca1-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bca1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bca1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bca1-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="4bca1-134">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4bca1-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
