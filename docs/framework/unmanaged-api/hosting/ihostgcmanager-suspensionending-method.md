---
title: IHostGCManager::SuspensionEnding – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 4c05ee766bf40be2e9c39f01c7e1b16cb9fab50d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804840"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="91fbb-102">IHostGCManager::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="91fbb-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="91fbb-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) obnovuje spouštění úloh na vláknech, které byly pozastaveny pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="91fbb-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91fbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91fbb-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91fbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91fbb-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="91fbb-106">pro Generování uvolňování paměti, které je právě dokončováno, ze kterého se vlákno obnovuje.</span><span class="sxs-lookup"><span data-stu-id="91fbb-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91fbb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="91fbb-107">Return Value</span></span>  
  
|<span data-ttu-id="91fbb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91fbb-108">HRESULT</span></span>|<span data-ttu-id="91fbb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="91fbb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91fbb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="91fbb-110">S_OK</span></span>|<span data-ttu-id="91fbb-111">`SuspensionEnding`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="91fbb-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="91fbb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91fbb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91fbb-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="91fbb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91fbb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91fbb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91fbb-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="91fbb-115">The call timed out.</span></span>|  
|<span data-ttu-id="91fbb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91fbb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91fbb-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="91fbb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91fbb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91fbb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91fbb-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="91fbb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91fbb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91fbb-120">E_FAIL</span></span>|<span data-ttu-id="91fbb-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="91fbb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91fbb-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="91fbb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91fbb-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91fbb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91fbb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91fbb-124">Remarks</span></span>  
 <span data-ttu-id="91fbb-125">Rozhraní CLR volá `SuspensionEnding` po provedení uvolňování paměti, aby informovalo hostitele, že vlákno pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="91fbb-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91fbb-126">Neměňte plán vlákna, ze kterého byla volána metoda.</span><span class="sxs-lookup"><span data-stu-id="91fbb-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91fbb-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91fbb-127">Requirements</span></span>  
 <span data-ttu-id="91fbb-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91fbb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91fbb-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91fbb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91fbb-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91fbb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91fbb-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91fbb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91fbb-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="91fbb-132">See also</span></span>

- [<span data-ttu-id="91fbb-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91fbb-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="91fbb-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91fbb-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="91fbb-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91fbb-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="91fbb-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91fbb-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="91fbb-137">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91fbb-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
