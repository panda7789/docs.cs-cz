---
title: "IHostTaskManager::Sleep – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.Sleep
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc26ca7d226c4529b0bc702567e774f2f98b085d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="632ed-102">IHostTaskManager::Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="632ed-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="632ed-103">Upozorní hostitele, že aktuální úlohy přechází do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="632ed-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="632ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="632ed-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="632ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="632ed-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="632ed-106">[v] Časový interval v milisekundách, která bude v režimu spánku vlákno.</span><span class="sxs-lookup"><span data-stu-id="632ed-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="632ed-107">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty výčtu, která určuje, jaké akce hostitele provést v případě, že tato akce bloky.</span><span class="sxs-lookup"><span data-stu-id="632ed-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="632ed-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="632ed-108">Return Value</span></span>  
  
|<span data-ttu-id="632ed-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="632ed-109">HRESULT</span></span>|<span data-ttu-id="632ed-110">Popis</span><span class="sxs-lookup"><span data-stu-id="632ed-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="632ed-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="632ed-111">S_OK</span></span>|<span data-ttu-id="632ed-112">`Sleep`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="632ed-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="632ed-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="632ed-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="632ed-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="632ed-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="632ed-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="632ed-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="632ed-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="632ed-116">The call timed out.</span></span>|  
|<span data-ttu-id="632ed-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="632ed-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="632ed-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="632ed-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="632ed-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="632ed-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="632ed-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="632ed-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="632ed-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="632ed-121">E_FAIL</span></span>|<span data-ttu-id="632ed-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="632ed-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="632ed-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="632ed-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="632ed-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="632ed-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="632ed-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="632ed-125">Remarks</span></span>  
 <span data-ttu-id="632ed-126">Modul CLR obvykle volá `IHostTaskManager::Sleep` při <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> je volání z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="632ed-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="632ed-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="632ed-127">Requirements</span></span>  
 <span data-ttu-id="632ed-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="632ed-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="632ed-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="632ed-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="632ed-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="632ed-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="632ed-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="632ed-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="632ed-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="632ed-132">See Also</span></span>  
 [<span data-ttu-id="632ed-133">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="632ed-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="632ed-134">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="632ed-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="632ed-135">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="632ed-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="632ed-136">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="632ed-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
