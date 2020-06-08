---
title: IHostSecurityManager::SetSecurityContext – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: 6a6b4d0351e22026dc873aad8281d0259d871a14
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501479"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="e01ee-102">IHostSecurityManager::SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="e01ee-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="e01ee-103">Nastaví kontext zabezpečení aktuálně zpracovávaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="e01ee-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e01ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e01ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e01ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e01ee-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="e01ee-106">pro Jedna z hodnot [EContextType –](econtexttype-enumeration.md) , která označuje typ kontextu, který modul CLR (Common Language Runtime) umísťuje na hostitele.</span><span class="sxs-lookup"><span data-stu-id="e01ee-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="e01ee-107">mimo Ukazatel na adresu nového objektu [IHostSecurityContext –](ihostsecuritycontext-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e01ee-107">[out] A pointer to the address of a new [IHostSecurityContext](ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e01ee-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e01ee-108">Return Value</span></span>  
  
|<span data-ttu-id="e01ee-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e01ee-109">HRESULT</span></span>|<span data-ttu-id="e01ee-110">Description</span><span class="sxs-lookup"><span data-stu-id="e01ee-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e01ee-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e01ee-111">S_OK</span></span>|<span data-ttu-id="e01ee-112">`SetSecurityContext`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e01ee-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="e01ee-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e01ee-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e01ee-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e01ee-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e01ee-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e01ee-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e01ee-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e01ee-116">The call timed out.</span></span>|  
|<span data-ttu-id="e01ee-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e01ee-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e01ee-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e01ee-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e01ee-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e01ee-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e01ee-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e01ee-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e01ee-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e01ee-121">E_FAIL</span></span>|<span data-ttu-id="e01ee-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e01ee-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e01ee-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e01ee-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e01ee-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e01ee-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e01ee-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e01ee-125">Remarks</span></span>  
 <span data-ttu-id="e01ee-126">CLR volá `SetSecurityContext` v několika scénářích.</span><span class="sxs-lookup"><span data-stu-id="e01ee-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="e01ee-127">Před tím, než se spustí třídy a konstruktory modulu a finalizační metody, vyvolá volání CLR `SetSecurityContext` k ochraně hostitele před selháním spuštění.</span><span class="sxs-lookup"><span data-stu-id="e01ee-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="e01ee-128">Poté obnoví kontext zabezpečení do původního stavu po provedení konstruktoru nebo finalizační metody pomocí jiného volání metody `SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="e01ee-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="e01ee-129">Podobný vzor se děje I v/v dokončování.</span><span class="sxs-lookup"><span data-stu-id="e01ee-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="e01ee-130">Pokud hostitel implementuje [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), VYVOLÁ volání CLR `SetSecurityContext` po volání [ICLRIoCompletionManager –::-Complete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="e01ee-130">If the host implements [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="e01ee-131">V asynchronních bodech v pracovních vláknech volání CLR v rámci `SetSecurityContext` <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), v závislosti na tom, zda hostitel nebo modul CLR implementuje fond vláken.</span><span class="sxs-lookup"><span data-stu-id="e01ee-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e01ee-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e01ee-132">Requirements</span></span>  
 <span data-ttu-id="e01ee-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e01ee-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e01ee-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e01ee-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e01ee-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e01ee-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e01ee-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e01ee-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01ee-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e01ee-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="e01ee-138">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="e01ee-138">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="e01ee-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e01ee-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e01ee-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e01ee-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="e01ee-141">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e01ee-141">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e01ee-142">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e01ee-142">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="e01ee-143">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e01ee-143">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
