---
title: "ICLRTask::SetTaskIdentifier – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SetTaskIdentifier
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 916f4638ad8206352f3b5973bb6c8b5dab39cda4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="e186f-102">ICLRTask::SetTaskIdentifier – metoda</span><span class="sxs-lookup"><span data-stu-id="e186f-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="e186f-103">Dá pokyn, modul CLR (CLR) pro přidružení hodnota zadaného identifikátoru úlohy reprezentována aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="e186f-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e186f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e186f-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e186f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e186f-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="e186f-106">[v] Jedinečný identifikátor pro modul common language runtime pro přidružení úlohy reprezentována aktuální `ICLRTask` instance.</span><span class="sxs-lookup"><span data-stu-id="e186f-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e186f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e186f-107">Return Value</span></span>  
  
|<span data-ttu-id="e186f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e186f-108">HRESULT</span></span>|<span data-ttu-id="e186f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e186f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e186f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e186f-110">S_OK</span></span>|<span data-ttu-id="e186f-111">`SetTaskIdentifier`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e186f-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="e186f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e186f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e186f-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e186f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e186f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e186f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e186f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e186f-115">The call timed out.</span></span>|  
|<span data-ttu-id="e186f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e186f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e186f-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e186f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e186f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e186f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e186f-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e186f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e186f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e186f-120">E_FAIL</span></span>|<span data-ttu-id="e186f-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e186f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e186f-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e186f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e186f-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e186f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e186f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e186f-124">Remarks</span></span>  
 <span data-ttu-id="e186f-125">Hostitele možné přidružit identifikátor úlohu usnadňuje integraci modulu CLR a hostitele v prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="e186f-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="e186f-126">Identifikátor nemá žádný význam pro modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e186f-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="e186f-127">Modul CLR předá podél aplikace ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e186f-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="e186f-128">Ladicí program můžete použít tento identifikátor zásobník volání CLR přidružit zásobník volání hostitele a povolit jejich odpovídajících trasování informace, které se unified při zobrazení v uživatelském rozhraní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e186f-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e186f-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e186f-129">Requirements</span></span>  
 <span data-ttu-id="e186f-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e186f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e186f-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e186f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e186f-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e186f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e186f-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e186f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e186f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e186f-134">See Also</span></span>  
 [<span data-ttu-id="e186f-135">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e186f-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e186f-136">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e186f-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e186f-137">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e186f-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e186f-138">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e186f-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
