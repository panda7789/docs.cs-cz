---
title: IHostIoCompletionManager::GetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: a97a7abf4f561a5aba41d8019f2ba5bd8e879acd
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804741"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="62142-102">IHostIoCompletionManager::GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="62142-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="62142-103">Získá maximální počet vláken, která může hostitel Allot na požadavky na vstupně-výstupní operace služby.</span><span class="sxs-lookup"><span data-stu-id="62142-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62142-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62142-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62142-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62142-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="62142-106">mimo Ukazatel na maximální počet vláken ve fondu vláken, který může hostitel Allot na vstupně-výstupní požadavky služby.</span><span class="sxs-lookup"><span data-stu-id="62142-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62142-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62142-107">Return Value</span></span>  
  
|<span data-ttu-id="62142-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62142-108">HRESULT</span></span>|<span data-ttu-id="62142-109">Popis</span><span class="sxs-lookup"><span data-stu-id="62142-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62142-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="62142-110">S_OK</span></span>|<span data-ttu-id="62142-111">`GetMaxThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="62142-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="62142-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62142-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62142-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="62142-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62142-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62142-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62142-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="62142-115">The call timed out.</span></span>|  
|<span data-ttu-id="62142-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62142-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62142-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="62142-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62142-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62142-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62142-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="62142-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62142-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62142-120">E_FAIL</span></span>|<span data-ttu-id="62142-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="62142-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62142-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="62142-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62142-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="62142-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="62142-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="62142-124">E_NOTIMPL</span></span>|<span data-ttu-id="62142-125">Hostitel neposkytuje implementaci `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="62142-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62142-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62142-126">Remarks</span></span>  
 <span data-ttu-id="62142-127">Hostitel může chtít exkluzivní kontrolu nad počtem vláken, která je možné přiděluje zpracování vstupně-výstupních požadavků, z důvodů, jako je implementace, výkon nebo škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="62142-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="62142-128">Z tohoto důvodu není nutné implementovat hostitele `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="62142-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="62142-129">V takovém případě by měl hostitel vracet E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="62142-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62142-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62142-130">Requirements</span></span>  
 <span data-ttu-id="62142-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62142-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62142-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="62142-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62142-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="62142-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62142-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62142-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62142-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="62142-135">See also</span></span>

- [<span data-ttu-id="62142-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62142-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="62142-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62142-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
