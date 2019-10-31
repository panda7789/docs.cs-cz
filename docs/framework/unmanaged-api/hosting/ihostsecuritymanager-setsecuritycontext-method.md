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
ms.openlocfilehash: 676a1d50202333203c13fcf916dbb14a6d91fb8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121448"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="4e7da-102">IHostSecurityManager::SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="4e7da-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="4e7da-103">Nastaví kontext zabezpečení aktuálně zpracovávaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="4e7da-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e7da-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e7da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e7da-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="4e7da-106">pro Jedna z hodnot [EContextType –](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) , která označuje typ kontextu, který modul CLR (Common Language Runtime) umísťuje na hostitele.</span><span class="sxs-lookup"><span data-stu-id="4e7da-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="4e7da-107">mimo Ukazatel na adresu nového objektu [IHostSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4e7da-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e7da-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4e7da-108">Return Value</span></span>  
  
|<span data-ttu-id="4e7da-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e7da-109">HRESULT</span></span>|<span data-ttu-id="4e7da-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4e7da-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e7da-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e7da-111">S_OK</span></span>|<span data-ttu-id="4e7da-112">`SetSecurityContext` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4e7da-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="4e7da-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4e7da-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4e7da-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4e7da-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4e7da-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4e7da-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4e7da-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4e7da-116">The call timed out.</span></span>|  
|<span data-ttu-id="4e7da-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e7da-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4e7da-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="4e7da-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4e7da-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4e7da-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4e7da-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="4e7da-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4e7da-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4e7da-121">E_FAIL</span></span>|<span data-ttu-id="4e7da-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4e7da-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4e7da-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4e7da-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4e7da-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4e7da-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7da-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e7da-125">Remarks</span></span>  
 <span data-ttu-id="4e7da-126">CLR volá `SetSecurityContext` v několika scénářích.</span><span class="sxs-lookup"><span data-stu-id="4e7da-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="4e7da-127">Před tím, než se spustí třídy a konstruktory modulu a finalizační metody, vyvolá CLR `SetSecurityContext` k ochraně hostitele před selháním spuštění.</span><span class="sxs-lookup"><span data-stu-id="4e7da-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="4e7da-128">Poté obnoví kontext zabezpečení do původního stavu po provedení konstruktoru nebo finalizační metody pomocí jiného volání `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="4e7da-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="4e7da-129">Podobný vzor se děje I v/v dokončování.</span><span class="sxs-lookup"><span data-stu-id="4e7da-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="4e7da-130">Pokud hostitel implementuje [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), CLR volá `SetSecurityContext` po volání [ICLRIoCompletionManager –::-Complete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="4e7da-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="4e7da-131">V asynchronních bodech v pracovních vláknech volá CLR `SetSecurityContext` v rámci <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> nebo uvnitř [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), podle toho, zda hostitel nebo modul CLR implementuje fond vláken.</span><span class="sxs-lookup"><span data-stu-id="4e7da-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e7da-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e7da-132">Requirements</span></span>  
 <span data-ttu-id="4e7da-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7da-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7da-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e7da-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e7da-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e7da-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e7da-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7da-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7da-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e7da-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="4e7da-138">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="4e7da-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="4e7da-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7da-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4e7da-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7da-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="4e7da-141">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7da-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="4e7da-142">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7da-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="4e7da-143">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e7da-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
