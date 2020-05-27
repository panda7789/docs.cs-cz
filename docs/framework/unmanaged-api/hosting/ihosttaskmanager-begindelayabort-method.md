---
title: IHostTaskManager::BeginDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: ea3269d06fdd3f5a2e365465d45ba6e569127b0a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842371"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="f3145-102">IHostTaskManager::BeginDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="f3145-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="f3145-103">Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém musí být aktuální úloha přerušena.</span><span class="sxs-lookup"><span data-stu-id="f3145-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3145-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3145-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f3145-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f3145-105">Return Value</span></span>  
  
|<span data-ttu-id="f3145-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3145-106">HRESULT</span></span>|<span data-ttu-id="f3145-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f3145-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3145-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3145-108">S_OK</span></span>|<span data-ttu-id="f3145-109">`BeginDelayAbort`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f3145-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f3145-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3145-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3145-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f3145-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3145-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3145-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3145-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f3145-113">The call timed out.</span></span>|  
|<span data-ttu-id="f3145-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3145-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3145-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f3145-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3145-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3145-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3145-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f3145-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3145-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3145-118">E_FAIL</span></span>|<span data-ttu-id="f3145-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f3145-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3145-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f3145-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3145-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f3145-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f3145-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f3145-122">E_UNEXPECTED</span></span>|<span data-ttu-id="f3145-123">`BeginDelayAbort`již byla volána, ale odpovídající volání [EndDelayAbort –](ihosttaskmanager-enddelayabort-method.md) ještě nebylo přijato.</span><span class="sxs-lookup"><span data-stu-id="f3145-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3145-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3145-124">Remarks</span></span>  
 <span data-ttu-id="f3145-125">Hostitel nesmí přerušit aktuální úlohu, dokud `EndDelayAbort` není volána.</span><span class="sxs-lookup"><span data-stu-id="f3145-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="f3145-126">Pokud je provedeno jiné volání bez nabývání `BeginDelayAbort` volání `EndDelayAbort` , hostitel by měl vracet E_UNEXPECTED z `BeginDelayAbort` a nesmí mít žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="f3145-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3145-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3145-127">Requirements</span></span>  
 <span data-ttu-id="f3145-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3145-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3145-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3145-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3145-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3145-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3145-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3145-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3145-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3145-132">See also</span></span>

- [<span data-ttu-id="f3145-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3145-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f3145-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3145-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f3145-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3145-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
