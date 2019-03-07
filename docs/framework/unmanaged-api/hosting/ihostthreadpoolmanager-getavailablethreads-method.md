---
title: IHostThreadPoolManager::GetAvailableThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f9eb28ea1a60991d047494336035aaf239b9edd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478593"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="92a6a-102">IHostThreadPoolManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="92a6a-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="92a6a-103">Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="92a6a-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92a6a-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92a6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92a6a-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="92a6a-106">[out] Ukazatel na počet vláken ve fondu vláken, které nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="92a6a-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92a6a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92a6a-107">Return Value</span></span>  
  
|<span data-ttu-id="92a6a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92a6a-108">HRESULT</span></span>|<span data-ttu-id="92a6a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="92a6a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92a6a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="92a6a-110">S_OK</span></span>|<span data-ttu-id="92a6a-111">`GetAvailableThreads` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="92a6a-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="92a6a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92a6a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92a6a-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="92a6a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92a6a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92a6a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92a6a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="92a6a-115">The call timed out.</span></span>|  
|<span data-ttu-id="92a6a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92a6a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92a6a-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="92a6a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92a6a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92a6a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92a6a-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="92a6a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92a6a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92a6a-120">E_FAIL</span></span>|<span data-ttu-id="92a6a-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="92a6a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92a6a-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="92a6a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92a6a-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92a6a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92a6a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="92a6a-124">E_NOTIMPL</span></span>|<span data-ttu-id="92a6a-125">Hostitel neposkytuje implementaci `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="92a6a-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92a6a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92a6a-126">Remarks</span></span>  
 <span data-ttu-id="92a6a-127">Pokud hostitel neposkytuje implementaci `GetAvailableThreads`, měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="92a6a-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92a6a-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92a6a-128">Requirements</span></span>  
 <span data-ttu-id="92a6a-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92a6a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92a6a-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92a6a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92a6a-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92a6a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92a6a-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92a6a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a6a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92a6a-133">See also</span></span>
- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="92a6a-134">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92a6a-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
