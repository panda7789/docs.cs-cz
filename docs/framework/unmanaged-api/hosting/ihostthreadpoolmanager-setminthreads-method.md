---
title: IHostThreadPoolManager::SetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d0e8198fece4a718b6478f199820738d49ed988
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519837"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="78a87-102">IHostThreadPoolManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="78a87-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="78a87-103">Nastaví minimální počet nečinných vláken, které hostitele, musíte mít v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="78a87-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78a87-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78a87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78a87-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="78a87-106">[in] Nový minimální počet vláken, která se musí spravovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="78a87-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78a87-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a87-107">Return Value</span></span>  
  
|<span data-ttu-id="78a87-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78a87-108">HRESULT</span></span>|<span data-ttu-id="78a87-109">Popis</span><span class="sxs-lookup"><span data-stu-id="78a87-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78a87-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="78a87-110">S_OK</span></span>|<span data-ttu-id="78a87-111">`SetMinThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="78a87-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="78a87-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78a87-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78a87-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="78a87-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78a87-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78a87-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78a87-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="78a87-115">The call timed out.</span></span>|  
|<span data-ttu-id="78a87-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78a87-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78a87-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="78a87-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78a87-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78a87-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78a87-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="78a87-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78a87-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78a87-120">E_FAIL</span></span>|<span data-ttu-id="78a87-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="78a87-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78a87-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="78a87-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78a87-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78a87-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78a87-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="78a87-124">E_NOTIMPL</span></span>|<span data-ttu-id="78a87-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="78a87-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78a87-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78a87-126">Remarks</span></span>  
 <span data-ttu-id="78a87-127">Hostitel není potřeba zajišťovat implementaci rozhraní `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="78a87-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="78a87-128">V tomto případě měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="78a87-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a87-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78a87-129">Requirements</span></span>  
 <span data-ttu-id="78a87-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78a87-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78a87-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78a87-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78a87-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78a87-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78a87-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78a87-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a87-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78a87-134">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="78a87-135">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="78a87-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="78a87-136">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="78a87-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="78a87-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78a87-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
