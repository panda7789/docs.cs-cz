---
title: IHostThreadPoolManager::GetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f4c2ea6deadeb0e9e1869a4ab064f2a948a74f4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749213"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="76fd1-102">IHostThreadPoolManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="76fd1-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="76fd1-103">Získá minimální počet nečinných vláken, které udržuje hostitele ve fondu vláken čekat na případná požadavků.</span><span class="sxs-lookup"><span data-stu-id="76fd1-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76fd1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76fd1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76fd1-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="76fd1-106">[out] Ukazatel na minimální počet nečinných pracovních vláken, které aktuálně uchovává hostitele.</span><span class="sxs-lookup"><span data-stu-id="76fd1-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76fd1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="76fd1-107">Return Value</span></span>  
  
|<span data-ttu-id="76fd1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76fd1-108">HRESULT</span></span>|<span data-ttu-id="76fd1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="76fd1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76fd1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="76fd1-110">S_OK</span></span>|<span data-ttu-id="76fd1-111">`GetMinThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="76fd1-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="76fd1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76fd1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76fd1-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="76fd1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76fd1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76fd1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76fd1-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="76fd1-115">The call timed out.</span></span>|  
|<span data-ttu-id="76fd1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76fd1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76fd1-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="76fd1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76fd1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76fd1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76fd1-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="76fd1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76fd1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76fd1-120">E_FAIL</span></span>|<span data-ttu-id="76fd1-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="76fd1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76fd1-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="76fd1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76fd1-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76fd1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="76fd1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="76fd1-124">E_NOTIMPL</span></span>|<span data-ttu-id="76fd1-125">Hostitel neposkytuje implementaci `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="76fd1-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76fd1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76fd1-126">Remarks</span></span>  
 <span data-ttu-id="76fd1-127">Hostitel není potřeba zajišťovat implementaci rozhraní `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="76fd1-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="76fd1-128">V tomto případě měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="76fd1-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76fd1-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76fd1-129">Requirements</span></span>  
 <span data-ttu-id="76fd1-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76fd1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76fd1-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76fd1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76fd1-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76fd1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76fd1-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76fd1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76fd1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76fd1-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="76fd1-135">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="76fd1-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="76fd1-136">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="76fd1-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="76fd1-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76fd1-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
