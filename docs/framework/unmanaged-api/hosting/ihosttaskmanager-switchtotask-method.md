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
ms.openlocfilehash: a55b43f3629cebb0ba1d3a7ac1802126874418d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122120"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="01309-102">IHostTaskManager::SwitchToTask – metoda</span><span class="sxs-lookup"><span data-stu-id="01309-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="01309-103">Upozorňuje hostitele, že by měl přepnout aktuální úlohu.</span><span class="sxs-lookup"><span data-stu-id="01309-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01309-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01309-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01309-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01309-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="01309-106">pro Jedna z hodnot výčtu [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , která určuje akci, kterou by měl hostitel provést, pokud se zablokuje požadovaná operace.</span><span class="sxs-lookup"><span data-stu-id="01309-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01309-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01309-107">Return Value</span></span>  
  
|<span data-ttu-id="01309-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01309-108">HRESULT</span></span>|<span data-ttu-id="01309-109">Popis</span><span class="sxs-lookup"><span data-stu-id="01309-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01309-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="01309-110">S_OK</span></span>|<span data-ttu-id="01309-111">`SwitchToTask` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="01309-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="01309-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01309-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01309-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="01309-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01309-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01309-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01309-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="01309-115">The call timed out.</span></span>|  
|<span data-ttu-id="01309-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01309-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01309-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="01309-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01309-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01309-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01309-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="01309-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01309-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01309-120">E_FAIL</span></span>|<span data-ttu-id="01309-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="01309-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01309-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="01309-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01309-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01309-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01309-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01309-124">Remarks</span></span>  
 <span data-ttu-id="01309-125">Hostitel může v případě potřeby přepnout na jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="01309-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01309-126">`SwitchToTask` neurčuje, na kterou úlohu má hostitel přepnout; Určuje pouze úkol, ze kterého by se měl přepnout.</span><span class="sxs-lookup"><span data-stu-id="01309-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01309-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01309-127">Requirements</span></span>  
 <span data-ttu-id="01309-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01309-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01309-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01309-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01309-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01309-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01309-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01309-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01309-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01309-132">See also</span></span>

- [<span data-ttu-id="01309-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01309-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="01309-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01309-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="01309-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01309-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="01309-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01309-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
