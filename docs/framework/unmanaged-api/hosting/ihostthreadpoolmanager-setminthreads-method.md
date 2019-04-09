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
ms.openlocfilehash: e290f20feacc59944bb1cafded327f4316ab88d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174158"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="5c65b-102">IHostThreadPoolManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="5c65b-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="5c65b-103">Nastaví minimální počet nečinných vláken, které hostitele, musíte mít v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="5c65b-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c65b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c65b-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c65b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c65b-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="5c65b-106">[in] Nový minimální počet vláken, která se musí spravovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="5c65b-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c65b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c65b-107">Return Value</span></span>  
  
|<span data-ttu-id="5c65b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c65b-108">HRESULT</span></span>|<span data-ttu-id="5c65b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5c65b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c65b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c65b-110">S_OK</span></span>|`SetMinThreads` <span data-ttu-id="5c65b-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5c65b-111">returned successfully.</span></span>|  
|<span data-ttu-id="5c65b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c65b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c65b-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5c65b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c65b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c65b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c65b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5c65b-115">The call timed out.</span></span>|  
|<span data-ttu-id="5c65b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c65b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c65b-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="5c65b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c65b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c65b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c65b-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="5c65b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c65b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c65b-120">E_FAIL</span></span>|<span data-ttu-id="5c65b-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="5c65b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c65b-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5c65b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c65b-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c65b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c65b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5c65b-124">E_NOTIMPL</span></span>|<span data-ttu-id="5c65b-125">Hostitel neposkytuje implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5c65b-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c65b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c65b-126">Remarks</span></span>  
 <span data-ttu-id="5c65b-127">Hostitel není potřeba zajišťovat implementaci rozhraní `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="5c65b-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="5c65b-128">V tomto případě měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5c65b-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c65b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c65b-129">Requirements</span></span>  
 <span data-ttu-id="5c65b-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c65b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c65b-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c65b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c65b-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c65b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5c65b-133">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5c65b-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5c65b-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c65b-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="5c65b-135">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="5c65b-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="5c65b-136">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="5c65b-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="5c65b-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c65b-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
