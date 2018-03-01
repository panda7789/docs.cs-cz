---
title: "IHostSecurityManager::SetSecurityContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29a7652e20c08b9de584a9e11ac343ad92f40653
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="8866c-102">IHostSecurityManager::SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8866c-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="8866c-103">Nastaví kontext zabezpečení aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="8866c-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8866c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8866c-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8866c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8866c-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="8866c-106">[v] Jeden z [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) hodnoty, která určuje, jaké typy kontextu common language runtime (CLR) je umístění na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="8866c-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="8866c-107">[out] Ukazatel na adresu nového [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="8866c-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8866c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8866c-108">Return Value</span></span>  
  
|<span data-ttu-id="8866c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8866c-109">HRESULT</span></span>|<span data-ttu-id="8866c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8866c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8866c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8866c-111">S_OK</span></span>|<span data-ttu-id="8866c-112">`SetSecurityContext`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8866c-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="8866c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8866c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8866c-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8866c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8866c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8866c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8866c-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8866c-116">The call timed out.</span></span>|  
|<span data-ttu-id="8866c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8866c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8866c-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="8866c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8866c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8866c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8866c-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="8866c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8866c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8866c-121">E_FAIL</span></span>|<span data-ttu-id="8866c-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="8866c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8866c-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8866c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8866c-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8866c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8866c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8866c-125">Remarks</span></span>  
 <span data-ttu-id="8866c-126">Volání CLR `SetSecurityContext` několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="8866c-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="8866c-127">Než se provede, třídy a modul konstruktory a finalizační metody, modul CLR volá `SetSecurityContext` k ochraně hostitele selhání spuštění.</span><span class="sxs-lookup"><span data-stu-id="8866c-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="8866c-128">Potom obnoví kontext zabezpečení do původního stavu po spuštění konstruktoru nebo finalizační metodu, pomocí jiným voláním `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="8866c-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="8866c-129">Podobný Princip vyskytuje v dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="8866c-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="8866c-130">Pokud hostitel implementuje [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), volání CLR `SetSecurityContext` po volání hostitele [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="8866c-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="8866c-131">V asynchronní bodech v pracovních vláken, modul CLR volá `SetSecurityContext` v rámci <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> nebo uvnitř [ihostthreadpoolmanager::QueueUserWorkItem –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), v závislosti na tom, jestli je fond vláken implementace modulu CLR nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="8866c-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8866c-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8866c-132">Requirements</span></span>  
 <span data-ttu-id="8866c-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8866c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8866c-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8866c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8866c-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8866c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8866c-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8866c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8866c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="8866c-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="8866c-138">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="8866c-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="8866c-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8866c-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="8866c-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8866c-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="8866c-141">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8866c-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="8866c-142">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8866c-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="8866c-143">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8866c-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
