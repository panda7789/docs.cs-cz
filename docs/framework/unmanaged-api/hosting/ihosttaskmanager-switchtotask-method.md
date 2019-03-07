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
ms.openlocfilehash: 7e2d5c299814202d0a3a8ff1da577fdfd17801e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471998"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="0ccfc-102">IHostTaskManager::SwitchToTask – metoda</span><span class="sxs-lookup"><span data-stu-id="0ccfc-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="0ccfc-103">Upozorňuje hostitele, že by měla přepnutí aktuálního úkolu.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ccfc-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ccfc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ccfc-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="0ccfc-106">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnot výčtu označující akce by hostitele zabrat Pokud bloky požadovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ccfc-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0ccfc-107">Return Value</span></span>  
  
|<span data-ttu-id="0ccfc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ccfc-108">HRESULT</span></span>|<span data-ttu-id="0ccfc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0ccfc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ccfc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ccfc-110">S_OK</span></span>|<span data-ttu-id="0ccfc-111">`SwitchToTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="0ccfc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ccfc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ccfc-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ccfc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ccfc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ccfc-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ccfc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ccfc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ccfc-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ccfc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ccfc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ccfc-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ccfc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ccfc-120">E_FAIL</span></span>|<span data-ttu-id="0ccfc-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ccfc-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ccfc-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ccfc-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ccfc-124">Remarks</span></span>  
 <span data-ttu-id="0ccfc-125">Hostitele můžete přepínat do jiného úkolu jako požadované nebo potřebné.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ccfc-126">`SwitchToTask` jaké úlohy hostitele přepnout do; neurčuje Určuje pouze úloha, která by měla přepnutí z.</span><span class="sxs-lookup"><span data-stu-id="0ccfc-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ccfc-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ccfc-127">Requirements</span></span>  
 <span data-ttu-id="0ccfc-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ccfc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ccfc-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ccfc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ccfc-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ccfc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ccfc-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ccfc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccfc-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ccfc-132">See also</span></span>
- [<span data-ttu-id="0ccfc-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ccfc-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0ccfc-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ccfc-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0ccfc-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ccfc-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0ccfc-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ccfc-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
