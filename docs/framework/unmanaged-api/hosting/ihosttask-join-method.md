---
title: "IHostTask::Join – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Join
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5dbfcfc87a520925f36e09d4f2d21dbffadfe1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="ab8c1-102">IHostTask::Join – metoda</span><span class="sxs-lookup"><span data-stu-id="ab8c1-102">IHostTask::Join Method</span></span>
<span data-ttu-id="ab8c1-103">Blokuje volání úkolů dokud je úloha reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance dokončí, uplynutí zadaného časového intervalu nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab8c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab8c1-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab8c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab8c1-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="ab8c1-106">[v] Časový interval v milisekundách pro čekání úlohu ukončit.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="ab8c1-107">Pokud tento interval uplynutí se ukončí úlohu, odblokuje volání úkolů.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="ab8c1-108">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="ab8c1-109">Hodnota WAIT_ALERTABLE dá pokyn hostitele probuzení úlohu, pokud `Alert` je volána před provedením `milliseconds` uplynutí.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab8c1-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab8c1-110">Return Value</span></span>  
  
|<span data-ttu-id="ab8c1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab8c1-111">HRESULT</span></span>|<span data-ttu-id="ab8c1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ab8c1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab8c1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab8c1-113">S_OK</span></span>|<span data-ttu-id="ab8c1-114">`Join`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="ab8c1-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ab8c1-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ab8c1-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ab8c1-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ab8c1-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ab8c1-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-118">The call timed out.</span></span>|  
|<span data-ttu-id="ab8c1-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ab8c1-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ab8c1-120">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ab8c1-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ab8c1-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ab8c1-122">Událost byla zrušena při blokované vlákna nebo fiber čekal na nebo aktuální `IHostTask` instance není spojen s úlohu.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="ab8c1-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ab8c1-123">E_FAIL</span></span>|<span data-ttu-id="ab8c1-124">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ab8c1-125">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ab8c1-126">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ab8c1-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab8c1-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab8c1-127">Requirements</span></span>  
 <span data-ttu-id="ab8c1-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab8c1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab8c1-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab8c1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab8c1-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab8c1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab8c1-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab8c1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8c1-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab8c1-132">See Also</span></span>  
 [<span data-ttu-id="ab8c1-133">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab8c1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ab8c1-134">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab8c1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ab8c1-135">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab8c1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ab8c1-136">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab8c1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="ab8c1-137">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="ab8c1-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
