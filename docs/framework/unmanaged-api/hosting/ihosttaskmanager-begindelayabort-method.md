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
ms.openlocfilehash: b765d5449cebbdec5f106a8e4743fee2f0ee5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133137"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="f16d5-102">IHostTaskManager::BeginDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="f16d5-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="f16d5-103">Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém musí být aktuální úloha přerušena.</span><span class="sxs-lookup"><span data-stu-id="f16d5-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f16d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f16d5-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f16d5-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f16d5-105">Return Value</span></span>  
  
|<span data-ttu-id="f16d5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f16d5-106">HRESULT</span></span>|<span data-ttu-id="f16d5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f16d5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f16d5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f16d5-108">S_OK</span></span>|<span data-ttu-id="f16d5-109">`BeginDelayAbort` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f16d5-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f16d5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f16d5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f16d5-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f16d5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f16d5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f16d5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f16d5-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f16d5-113">The call timed out.</span></span>|  
|<span data-ttu-id="f16d5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f16d5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f16d5-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f16d5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f16d5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f16d5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f16d5-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f16d5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f16d5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f16d5-118">E_FAIL</span></span>|<span data-ttu-id="f16d5-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f16d5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f16d5-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f16d5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f16d5-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f16d5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f16d5-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f16d5-122">E_UNEXPECTED</span></span>|<span data-ttu-id="f16d5-123">`BeginDelayAbort` už je zavolaná, ale odpovídající volání [EndDelayAbort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) ještě není přijaté.</span><span class="sxs-lookup"><span data-stu-id="f16d5-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f16d5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f16d5-124">Remarks</span></span>  
 <span data-ttu-id="f16d5-125">Hostitel nesmí přerušit aktuální úlohu, dokud není volána `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="f16d5-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="f16d5-126">Pokud je provedeno jiné volání `BeginDelayAbort` bez navázání volání `EndDelayAbort`, hostitel by měl vrátit E_UNEXPECTED z `BeginDelayAbort`a neměla by mít žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="f16d5-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f16d5-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f16d5-127">Requirements</span></span>  
 <span data-ttu-id="f16d5-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f16d5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f16d5-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f16d5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f16d5-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f16d5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f16d5-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f16d5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f16d5-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f16d5-132">See also</span></span>

- [<span data-ttu-id="f16d5-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f16d5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f16d5-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f16d5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f16d5-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f16d5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
