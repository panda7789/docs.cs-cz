---
title: "IHostTaskManager::SwitchToTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SwitchToTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03578a6a9579a807323d54308347f16f24ae90dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="1d39d-102">IHostTaskManager::SwitchToTask – metoda</span><span class="sxs-lookup"><span data-stu-id="1d39d-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="1d39d-103">Upozorní hostitele, musí přepnout na aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="1d39d-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d39d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d39d-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d39d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d39d-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="1d39d-106">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty výčtu, který udává akci hostitele provést, pokud bloky požadovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="1d39d-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d39d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1d39d-107">Return Value</span></span>  
  
|<span data-ttu-id="1d39d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d39d-108">HRESULT</span></span>|<span data-ttu-id="1d39d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1d39d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d39d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d39d-110">S_OK</span></span>|<span data-ttu-id="1d39d-111">`SwitchToTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1d39d-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="1d39d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d39d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d39d-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1d39d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d39d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d39d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d39d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1d39d-115">The call timed out.</span></span>|  
|<span data-ttu-id="1d39d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d39d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d39d-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="1d39d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d39d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d39d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d39d-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="1d39d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d39d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d39d-120">E_FAIL</span></span>|<span data-ttu-id="1d39d-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="1d39d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d39d-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1d39d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d39d-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d39d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d39d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d39d-124">Remarks</span></span>  
 <span data-ttu-id="1d39d-125">Přepnout hostitele v jiné úloze jako požadovaný nebo potřebné.</span><span class="sxs-lookup"><span data-stu-id="1d39d-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d39d-126">`SwitchToTask`neurčuje který úkol hostitele by měl přepínače. Určuje pouze úloha, která by měla přejít z.</span><span class="sxs-lookup"><span data-stu-id="1d39d-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d39d-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d39d-127">Requirements</span></span>  
 <span data-ttu-id="1d39d-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d39d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d39d-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d39d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d39d-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d39d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d39d-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d39d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d39d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d39d-132">See Also</span></span>  
 [<span data-ttu-id="1d39d-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d39d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1d39d-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d39d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1d39d-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d39d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1d39d-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d39d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
