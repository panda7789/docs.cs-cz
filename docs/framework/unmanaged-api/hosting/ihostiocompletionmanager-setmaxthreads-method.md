---
title: IHostIoCompletionManager::SetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 55727903a7f3c798e7472de6de5249de98af7ae7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804672"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="09d18-102">IHostIoCompletionManager::SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="09d18-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="09d18-103">Nastaví maximální počet vláken, která hostitel allots na požadavky na vstupně-výstupní operace služby.</span><span class="sxs-lookup"><span data-stu-id="09d18-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09d18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09d18-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09d18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09d18-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="09d18-106">pro Maximální počet vláken, která se mají Allot pro vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="09d18-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09d18-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="09d18-107">Return Value</span></span>  
  
|<span data-ttu-id="09d18-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09d18-108">HRESULT</span></span>|<span data-ttu-id="09d18-109">Popis</span><span class="sxs-lookup"><span data-stu-id="09d18-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09d18-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="09d18-110">S_OK</span></span>|<span data-ttu-id="09d18-111">`SetMaxThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="09d18-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="09d18-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09d18-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09d18-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="09d18-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09d18-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09d18-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09d18-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="09d18-115">The call timed out.</span></span>|  
|<span data-ttu-id="09d18-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09d18-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09d18-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="09d18-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09d18-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09d18-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09d18-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="09d18-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09d18-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09d18-120">E_FAIL</span></span>|<span data-ttu-id="09d18-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="09d18-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09d18-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="09d18-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09d18-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="09d18-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09d18-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="09d18-124">E_NOTIMPL</span></span>|<span data-ttu-id="09d18-125">Hostitel neposkytuje implementaci `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="09d18-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09d18-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09d18-126">Remarks</span></span>  
 <span data-ttu-id="09d18-127">`SetMaxThreads`poskytuje modul CLR s příležitostí k nastavení maximálního počtu vláken, která jsou k dispozici pro žádosti o služby na vstupně-výstupních portech.</span><span class="sxs-lookup"><span data-stu-id="09d18-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="09d18-128">Hostitel může vyžadovat exkluzivní kontrolu velikosti fondu vláken, a to z důvodů, jako je implementace, výkon nebo škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="09d18-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="09d18-129">Z tohoto důvodu není nutné implementovat hostitele `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="09d18-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="09d18-130">V takovém případě by měl hostitel vracet E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="09d18-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09d18-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09d18-131">Requirements</span></span>  
 <span data-ttu-id="09d18-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09d18-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09d18-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09d18-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09d18-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="09d18-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09d18-135">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09d18-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09d18-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="09d18-136">See also</span></span>

- [<span data-ttu-id="09d18-137">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09d18-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="09d18-138">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09d18-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
