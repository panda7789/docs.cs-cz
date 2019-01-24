---
title: IHostThreadPoolManager::SetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 905ce9183d295568977eb7e216e5327d6b4ee8bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636089"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="c1160-102">IHostThreadPoolManager::SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c1160-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="c1160-103">Nastaví maximální počet vláken, které hostitele může udržovat ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="c1160-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1160-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1160-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1160-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1160-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="c1160-106">Maximální počet pracovních vláken ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="c1160-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1160-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1160-107">Return Value</span></span>  
  
|<span data-ttu-id="c1160-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1160-108">HRESULT</span></span>|<span data-ttu-id="c1160-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c1160-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1160-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1160-110">S_OK</span></span>|<span data-ttu-id="c1160-111">`SetMaxThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c1160-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="c1160-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1160-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1160-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c1160-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1160-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1160-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1160-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c1160-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1160-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1160-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1160-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c1160-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1160-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1160-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1160-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c1160-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1160-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1160-120">E_FAIL</span></span>|<span data-ttu-id="c1160-121">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c1160-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c1160-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c1160-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1160-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1160-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c1160-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c1160-124">E_NOTIMPL</span></span>|<span data-ttu-id="c1160-125">Hostitel neposkytuje implementaci `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="c1160-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1160-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1160-126">Remarks</span></span>  
 <span data-ttu-id="c1160-127">Hostitel není potřeba povolit modul CLR lze konfigurovat velikost fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="c1160-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="c1160-128">Někteří hostitelé může být vhodné výhradní kontrolu nad fondu vláken z důvodů, například provádění, výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="c1160-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="c1160-129">V takovém případě hostitele by měl vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c1160-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1160-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1160-130">Requirements</span></span>  
 <span data-ttu-id="c1160-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1160-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1160-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1160-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1160-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1160-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1160-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1160-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1160-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1160-135">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="c1160-136">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c1160-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="c1160-137">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c1160-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="c1160-138">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1160-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
