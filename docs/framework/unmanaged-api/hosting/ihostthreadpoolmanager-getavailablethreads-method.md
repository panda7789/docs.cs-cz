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
ms.openlocfilehash: 21449d9365e6260267d3c79f384f6136ce894821
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122087"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="44625-102">IHostThreadPoolManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="44625-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="44625-103">Získá počet vláken ve fondu vláken, které aktuálně nezpracovávají pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="44625-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44625-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44625-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44625-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44625-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="44625-106">mimo Ukazatel na počet vláken ve fondu vláken, který aktuálně nezpracovává pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="44625-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44625-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44625-107">Return Value</span></span>  
  
|<span data-ttu-id="44625-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44625-108">HRESULT</span></span>|<span data-ttu-id="44625-109">Popis</span><span class="sxs-lookup"><span data-stu-id="44625-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44625-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="44625-110">S_OK</span></span>|<span data-ttu-id="44625-111">`GetAvailableThreads` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="44625-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="44625-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44625-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44625-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="44625-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44625-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44625-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44625-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="44625-115">The call timed out.</span></span>|  
|<span data-ttu-id="44625-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44625-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44625-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="44625-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44625-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44625-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44625-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="44625-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44625-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44625-120">E_FAIL</span></span>|<span data-ttu-id="44625-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="44625-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44625-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="44625-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44625-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44625-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="44625-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="44625-124">E_NOTIMPL</span></span>|<span data-ttu-id="44625-125">Hostitel neposkytuje implementaci `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="44625-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44625-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44625-126">Remarks</span></span>  
 <span data-ttu-id="44625-127">Pokud hostitel neposkytuje implementaci `GetAvailableThreads`, měla by vrátit hodnotu HRESULT typu E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="44625-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44625-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44625-128">Requirements</span></span>  
 <span data-ttu-id="44625-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44625-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44625-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44625-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44625-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="44625-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44625-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44625-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44625-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44625-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="44625-134">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44625-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
