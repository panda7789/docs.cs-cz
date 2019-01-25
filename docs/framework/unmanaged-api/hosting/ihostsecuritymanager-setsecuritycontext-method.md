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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41b472d96c4db088c7ab34d9abb0940f3461c844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734552"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="4ed88-102">IHostSecurityManager::SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="4ed88-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="4ed88-103">Nastaví kontext zabezpečení aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="4ed88-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ed88-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ed88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ed88-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="4ed88-106">[in] Jeden z [econtexttype –](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) hodnoty určující, jaký typ kontextu common language runtime (CLR) je umístění na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="4ed88-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="4ed88-107">[out] Ukazatel na novou adresu [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="4ed88-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ed88-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ed88-108">Return Value</span></span>  
  
|<span data-ttu-id="4ed88-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ed88-109">HRESULT</span></span>|<span data-ttu-id="4ed88-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4ed88-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ed88-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ed88-111">S_OK</span></span>|<span data-ttu-id="4ed88-112">`SetSecurityContext` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4ed88-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="4ed88-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ed88-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ed88-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4ed88-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ed88-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ed88-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ed88-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4ed88-116">The call timed out.</span></span>|  
|<span data-ttu-id="4ed88-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ed88-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ed88-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="4ed88-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ed88-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ed88-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ed88-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="4ed88-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ed88-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ed88-121">E_FAIL</span></span>|<span data-ttu-id="4ed88-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="4ed88-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ed88-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4ed88-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ed88-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4ed88-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ed88-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ed88-125">Remarks</span></span>  
 <span data-ttu-id="4ed88-126">Volání CLR `SetSecurityContext` v několika situacích.</span><span class="sxs-lookup"><span data-stu-id="4ed88-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="4ed88-127">Než se provede, třídy a konstruktory modulu a finalizační metody, kterou volá CLR `SetSecurityContext` , která chrání hostitele selhání spuštění.</span><span class="sxs-lookup"><span data-stu-id="4ed88-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="4ed88-128">Potom resetuje kontextu zabezpečení do původního stavu po spuštění konstruktoru nebo finalizační metodu, pomocí jiného volání `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="4ed88-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="4ed88-129">Podobný vzorec dojde k dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="4ed88-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="4ed88-130">Pokud hostitel implementuje [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), volání CLR `SetSecurityContext` po volání hostitele [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="4ed88-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="4ed88-131">V asynchronní fázích pracovních vláken, kterou volá CLR `SetSecurityContext` v rámci <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> nebo v rámci [ihostthreadpoolmanager::QueueUserWorkItem –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)podle toho, jestli hostitel nebo modulu CLR je implementace fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="4ed88-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ed88-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ed88-132">Requirements</span></span>  
 <span data-ttu-id="4ed88-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ed88-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed88-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4ed88-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ed88-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ed88-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ed88-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed88-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed88-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ed88-137">See also</span></span>
- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="4ed88-138">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="4ed88-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="4ed88-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ed88-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4ed88-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ed88-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="4ed88-141">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ed88-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="4ed88-142">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ed88-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="4ed88-143">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ed88-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
