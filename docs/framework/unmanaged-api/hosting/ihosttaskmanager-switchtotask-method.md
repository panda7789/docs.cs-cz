---
title: IHostTaskManager::SwitchToTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4af3d73a4c45654d1d40ef2fbf44a0e2b3e1bf32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913717"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="5536e-102">IHostTaskManager::SwitchToTask – metoda</span><span class="sxs-lookup"><span data-stu-id="5536e-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="5536e-103">Upozorňuje hostitele, že by měl přepnout aktuální úlohu.</span><span class="sxs-lookup"><span data-stu-id="5536e-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5536e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5536e-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5536e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5536e-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="5536e-106">pro Jedna z hodnot výčtu [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , která určuje akci, kterou by měl hostitel provést, pokud se zablokuje požadovaná operace.</span><span class="sxs-lookup"><span data-stu-id="5536e-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5536e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5536e-107">Return Value</span></span>  
  
|<span data-ttu-id="5536e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5536e-108">HRESULT</span></span>|<span data-ttu-id="5536e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5536e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5536e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5536e-110">S_OK</span></span>|<span data-ttu-id="5536e-111">`SwitchToTask`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5536e-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="5536e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5536e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5536e-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5536e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5536e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5536e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5536e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5536e-115">The call timed out.</span></span>|  
|<span data-ttu-id="5536e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5536e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5536e-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="5536e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5536e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5536e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5536e-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="5536e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5536e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5536e-120">E_FAIL</span></span>|<span data-ttu-id="5536e-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="5536e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5536e-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="5536e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5536e-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5536e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5536e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5536e-124">Remarks</span></span>  
 <span data-ttu-id="5536e-125">Hostitel může v případě potřeby přepnout na jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="5536e-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5536e-126">`SwitchToTask`neurčuje, na kterou úlohu má hostitel přepnout; Určuje pouze úkol, ze kterého by se měl přepnout.</span><span class="sxs-lookup"><span data-stu-id="5536e-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5536e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5536e-127">Requirements</span></span>  
 <span data-ttu-id="5536e-128">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5536e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5536e-129">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5536e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5536e-130">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5536e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5536e-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5536e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5536e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5536e-132">See also</span></span>

- [<span data-ttu-id="5536e-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5536e-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5536e-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5536e-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5536e-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5536e-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5536e-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5536e-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
