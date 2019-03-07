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
ms.openlocfilehash: ed172ca9f10e941938ae43bd730a3fc6d658aca2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484638"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="4c7d3-102">IHostThreadPoolManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="4c7d3-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="4c7d3-103">Nastaví minimální počet nečinných vláken, které hostitele, musíte mít v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c7d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c7d3-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c7d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c7d3-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="4c7d3-106">[in] Nový minimální počet vláken, která se musí spravovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c7d3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c7d3-107">Return Value</span></span>  
  
|<span data-ttu-id="4c7d3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c7d3-108">HRESULT</span></span>|<span data-ttu-id="4c7d3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4c7d3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c7d3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c7d3-110">S_OK</span></span>|<span data-ttu-id="4c7d3-111">`SetMinThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4c7d3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c7d3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c7d3-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c7d3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c7d3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c7d3-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-115">The call timed out.</span></span>|  
|<span data-ttu-id="4c7d3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c7d3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c7d3-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c7d3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c7d3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c7d3-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c7d3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c7d3-120">E_FAIL</span></span>|<span data-ttu-id="4c7d3-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c7d3-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c7d3-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4c7d3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4c7d3-124">E_NOTIMPL</span></span>|<span data-ttu-id="4c7d3-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c7d3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c7d3-126">Remarks</span></span>  
 <span data-ttu-id="4c7d3-127">Hostitel není potřeba zajišťovat implementaci rozhraní `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="4c7d3-128">V tomto případě měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4c7d3-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c7d3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c7d3-129">Requirements</span></span>  
 <span data-ttu-id="4c7d3-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c7d3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c7d3-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c7d3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c7d3-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c7d3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c7d3-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c7d3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7d3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c7d3-134">See also</span></span>
- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4c7d3-135">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="4c7d3-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="4c7d3-136">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="4c7d3-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="4c7d3-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c7d3-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
