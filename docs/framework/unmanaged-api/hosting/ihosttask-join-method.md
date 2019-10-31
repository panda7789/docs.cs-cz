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
ms.openlocfilehash: dda68041dbf4efa82a35c48702d83aa231462fef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121374"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="38ebb-102">IHostTask::Join – metoda</span><span class="sxs-lookup"><span data-stu-id="38ebb-102">IHostTask::Join Method</span></span>
<span data-ttu-id="38ebb-103">Blokuje volající úlohu, dokud se nedokončí úkol, který je reprezentován aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , zadaný časový interval uplyne nebo [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="38ebb-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38ebb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38ebb-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38ebb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38ebb-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="38ebb-106">pro Časový interval (v milisekundách), po který se má čekat na ukončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="38ebb-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="38ebb-107">Pokud tento interval uplyne před ukončením úlohy, volající úkol odblokuje.</span><span class="sxs-lookup"><span data-stu-id="38ebb-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="38ebb-108">pro Jedna z hodnot [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="38ebb-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="38ebb-109">Hodnota WAIT_ALERTABLE dá hostiteli, aby probudit úlohu, pokud je zavolána `Alert` před uplynutím `milliseconds`.</span><span class="sxs-lookup"><span data-stu-id="38ebb-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38ebb-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38ebb-110">Return Value</span></span>  
  
|<span data-ttu-id="38ebb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38ebb-111">HRESULT</span></span>|<span data-ttu-id="38ebb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="38ebb-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38ebb-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="38ebb-113">S_OK</span></span>|<span data-ttu-id="38ebb-114">`Join` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="38ebb-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="38ebb-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38ebb-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38ebb-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="38ebb-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38ebb-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38ebb-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38ebb-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="38ebb-118">The call timed out.</span></span>|  
|<span data-ttu-id="38ebb-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38ebb-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38ebb-120">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="38ebb-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38ebb-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38ebb-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38ebb-122">Událost byla zrušena, zatímco na ní bylo zastaveno blokované vlákno nebo vlákno, nebo aktuální instance `IHostTask` není přidružena k úloze.</span><span class="sxs-lookup"><span data-stu-id="38ebb-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="38ebb-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38ebb-123">E_FAIL</span></span>|<span data-ttu-id="38ebb-124">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="38ebb-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38ebb-125">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="38ebb-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38ebb-126">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38ebb-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38ebb-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38ebb-127">Requirements</span></span>  
 <span data-ttu-id="38ebb-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38ebb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38ebb-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38ebb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38ebb-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38ebb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38ebb-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38ebb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ebb-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38ebb-132">See also</span></span>

- [<span data-ttu-id="38ebb-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38ebb-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="38ebb-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38ebb-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="38ebb-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38ebb-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="38ebb-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38ebb-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="38ebb-137">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="38ebb-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
