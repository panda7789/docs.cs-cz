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
ms.openlocfilehash: 8f9852034f6d8208bdaa9b424f689adc374bae2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443672"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="d4b2d-102">IHostThreadPoolManager::SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d4b2d-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="d4b2d-103">Nastaví minimální počet nečinných vláken, která musí zachovat hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b2d-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4b2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4b2d-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="d4b2d-106">[v] Nové minimální počet vláken, která musí zachovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4b2d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4b2d-107">Return Value</span></span>  
  
|<span data-ttu-id="d4b2d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4b2d-108">HRESULT</span></span>|<span data-ttu-id="d4b2d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b2d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4b2d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4b2d-110">S_OK</span></span>|<span data-ttu-id="d4b2d-111">`SetMinThreads` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d4b2d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4b2d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4b2d-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4b2d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4b2d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4b2d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-115">The call timed out.</span></span>|  
|<span data-ttu-id="d4b2d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4b2d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4b2d-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4b2d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4b2d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4b2d-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4b2d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4b2d-120">E_FAIL</span></span>|<span data-ttu-id="d4b2d-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4b2d-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4b2d-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d4b2d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d4b2d-124">E_NOTIMPL</span></span>|<span data-ttu-id="d4b2d-125">Hostitel neposkytuje implementace `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4b2d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4b2d-126">Remarks</span></span>  
 <span data-ttu-id="d4b2d-127">Hostitel není potřeba poskytnout implementaci `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="d4b2d-128">V takovém případě má být vrácen při použití hodnoty HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d4b2d-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b2d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4b2d-129">Requirements</span></span>  
 <span data-ttu-id="d4b2d-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4b2d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b2d-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4b2d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4b2d-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4b2d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4b2d-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4b2d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b2d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4b2d-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="d4b2d-135">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d4b2d-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="d4b2d-136">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d4b2d-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="d4b2d-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4b2d-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
