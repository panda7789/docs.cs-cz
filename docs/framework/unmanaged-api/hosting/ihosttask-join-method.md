---
title: IHostTask::Join – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4373fc4e8a4c414c40e8d3c5547b5998b9300348
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789516"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="a05ae-102">IHostTask::Join – metoda</span><span class="sxs-lookup"><span data-stu-id="a05ae-102">IHostTask::Join Method</span></span>
<span data-ttu-id="a05ae-103">Blokuje volající úlohou, dokud není úloha reprezentované aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance dokončení, o zadaný časový interval uplyne, nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="a05ae-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a05ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a05ae-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a05ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a05ae-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="a05ae-106">[in] Časový interval v milisekundách pro čekání na úlohu ukončit.</span><span class="sxs-lookup"><span data-stu-id="a05ae-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="a05ae-107">Pokud tento interval uplyne úlohy ukončí, odblokuje se volající úlohou.</span><span class="sxs-lookup"><span data-stu-id="a05ae-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="a05ae-108">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a05ae-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="a05ae-109">Hodnota WAIT_ALERTABLE dává pokyn hostitelského probuzení úkolu, pokud `Alert` je volána před provedením `milliseconds` uplyne.</span><span class="sxs-lookup"><span data-stu-id="a05ae-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a05ae-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a05ae-110">Return Value</span></span>  
  
|<span data-ttu-id="a05ae-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a05ae-111">HRESULT</span></span>|<span data-ttu-id="a05ae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a05ae-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a05ae-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a05ae-113">S_OK</span></span>|<span data-ttu-id="a05ae-114">`Join` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a05ae-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="a05ae-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a05ae-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a05ae-116">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a05ae-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a05ae-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a05ae-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a05ae-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a05ae-118">The call timed out.</span></span>|  
|<span data-ttu-id="a05ae-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a05ae-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a05ae-120">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a05ae-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a05ae-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a05ae-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a05ae-122">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na nebo aktuální `IHostTask` instance není přidružen k úkolu.</span><span class="sxs-lookup"><span data-stu-id="a05ae-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="a05ae-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a05ae-123">E_FAIL</span></span>|<span data-ttu-id="a05ae-124">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a05ae-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a05ae-125">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a05ae-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a05ae-126">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a05ae-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a05ae-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a05ae-127">Requirements</span></span>  
 <span data-ttu-id="a05ae-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a05ae-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a05ae-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a05ae-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a05ae-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a05ae-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a05ae-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a05ae-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05ae-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a05ae-132">See also</span></span>

- [<span data-ttu-id="a05ae-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a05ae-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a05ae-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a05ae-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a05ae-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a05ae-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a05ae-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a05ae-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="a05ae-137">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="a05ae-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
