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
ms.openlocfilehash: cc03960c2d45a6cf8aed58eaf048a0531decb08f
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842332"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="54799-102">IHostThreadPoolManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="54799-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="54799-103">Získá počet vláken ve fondu vláken, které aktuálně nezpracovávají pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="54799-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54799-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54799-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54799-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54799-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="54799-106">mimo Ukazatel na počet vláken ve fondu vláken, který aktuálně nezpracovává pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="54799-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54799-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="54799-107">Return Value</span></span>  
  
|<span data-ttu-id="54799-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54799-108">HRESULT</span></span>|<span data-ttu-id="54799-109">Popis</span><span class="sxs-lookup"><span data-stu-id="54799-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54799-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="54799-110">S_OK</span></span>|<span data-ttu-id="54799-111">`GetAvailableThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="54799-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="54799-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54799-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54799-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="54799-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54799-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54799-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54799-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="54799-115">The call timed out.</span></span>|  
|<span data-ttu-id="54799-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54799-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54799-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="54799-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54799-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54799-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54799-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="54799-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54799-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54799-120">E_FAIL</span></span>|<span data-ttu-id="54799-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="54799-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54799-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="54799-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54799-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="54799-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="54799-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="54799-124">E_NOTIMPL</span></span>|<span data-ttu-id="54799-125">Hostitel neposkytuje implementaci `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="54799-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54799-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54799-126">Remarks</span></span>  
 <span data-ttu-id="54799-127">Pokud hostitel neposkytuje implementaci `GetAvailableThreads` , měla by vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="54799-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54799-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54799-128">Requirements</span></span>  
 <span data-ttu-id="54799-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54799-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54799-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="54799-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54799-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54799-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54799-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54799-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54799-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="54799-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="54799-134">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54799-134">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
