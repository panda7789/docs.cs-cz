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
ms.openlocfilehash: 8fa59e065042565b4a543106fff714558cef42ec
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842241"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="5c4cd-102">IHostTask::Join – metoda</span><span class="sxs-lookup"><span data-stu-id="5c4cd-102">IHostTask::Join Method</span></span>
<span data-ttu-id="5c4cd-103">Blokuje volající úlohu, dokud se nedokončí úkol, který je reprezentován aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , zadaný časový interval uplyne nebo [IHostTask:: Alert](ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c4cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c4cd-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c4cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c4cd-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="5c4cd-106">pro Časový interval (v milisekundách), po který se má čekat na ukončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="5c4cd-107">Pokud tento interval uplyne před ukončením úlohy, volající úkol odblokuje.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="5c4cd-108">pro Jedna z hodnot [WAIT_OPTION](wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5c4cd-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="5c4cd-109">Hodnota WAIT_ALERTABLE instruuje hostitele, že má probudit úlohu, pokud `Alert` je volána před `milliseconds` uplynutím doby.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c4cd-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c4cd-110">Return Value</span></span>  
  
|<span data-ttu-id="5c4cd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c4cd-111">HRESULT</span></span>|<span data-ttu-id="5c4cd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5c4cd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c4cd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c4cd-113">S_OK</span></span>|<span data-ttu-id="5c4cd-114">`Join`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="5c4cd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c4cd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c4cd-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c4cd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c4cd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c4cd-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-118">The call timed out.</span></span>|  
|<span data-ttu-id="5c4cd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c4cd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c4cd-120">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c4cd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c4cd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c4cd-122">Událost byla zrušena, zatímco na ní bylo zastaveno blokované vlákno nebo vlákno, nebo aktuální `IHostTask` instance není přidružena k úloze.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="5c4cd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c4cd-123">E_FAIL</span></span>|<span data-ttu-id="5c4cd-124">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c4cd-125">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c4cd-126">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c4cd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c4cd-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c4cd-127">Requirements</span></span>  
 <span data-ttu-id="5c4cd-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c4cd-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c4cd-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5c4cd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c4cd-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5c4cd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c4cd-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c4cd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4cd-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c4cd-132">See also</span></span>

- [<span data-ttu-id="5c4cd-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c4cd-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5c4cd-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c4cd-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5c4cd-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c4cd-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5c4cd-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c4cd-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5c4cd-137">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="5c4cd-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
