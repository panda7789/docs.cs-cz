---
title: IHostIoCompletionManager::GetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: e748a731f2c6934f58a1cd838cc40ce4fd0e4652
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804724"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="3c8c6-102">IHostIoCompletionManager::GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="3c8c6-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="3c8c6-103">Získá minimální počet vláken, která hostitel poskytuje pro zpracování vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c8c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c8c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c8c6-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="3c8c6-106">mimo Ukazatel na minimální počet vláken, která hostitel poskytuje pro zpracování vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c8c6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3c8c6-107">Return Value</span></span>  
  
|<span data-ttu-id="3c8c6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c8c6-108">HRESULT</span></span>|<span data-ttu-id="3c8c6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3c8c6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c8c6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c8c6-110">S_OK</span></span>|<span data-ttu-id="3c8c6-111">`GetMinThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3c8c6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c8c6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c8c6-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c8c6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c8c6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c8c6-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-115">The call timed out.</span></span>|  
|<span data-ttu-id="3c8c6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c8c6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c8c6-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c8c6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c8c6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c8c6-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c8c6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c8c6-120">E_FAIL</span></span>|<span data-ttu-id="3c8c6-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c8c6-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c8c6-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3c8c6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3c8c6-124">E_NOTIMPL</span></span>|<span data-ttu-id="3c8c6-125">Hostitel neposkytuje implementaci `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="3c8c6-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c8c6-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c8c6-126">Remarks</span></span>  
 <span data-ttu-id="3c8c6-127">Hostitel může chtít exkluzivní kontrolu nad počtem vláken přidělených v/v požadavků služby, a to z důvodů, jako je implementace, výkon nebo škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3c8c6-128">Z tohoto důvodu není nutné implementovat hostitele `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="3c8c6-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="3c8c6-129">V takovém případě by měl hostitel vracet E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="3c8c6-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c8c6-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c8c6-130">Requirements</span></span>  
 <span data-ttu-id="3c8c6-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c8c6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c8c6-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c8c6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c8c6-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3c8c6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c8c6-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c8c6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8c6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c8c6-135">See also</span></span>

- [<span data-ttu-id="3c8c6-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c8c6-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3c8c6-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c8c6-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
