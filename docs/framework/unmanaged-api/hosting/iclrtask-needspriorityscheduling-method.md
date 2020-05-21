---
title: ICLRTask::NeedsPriorityScheduling – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: df20e98a9e88c10bac748a5acfc91adcb133da79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762986"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="536cf-102">ICLRTask::NeedsPriorityScheduling – metoda</span><span class="sxs-lookup"><span data-stu-id="536cf-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="536cf-103">Načte hodnotu, která indikuje, jestli aktuální úkol, který se má přepnout, musí být označený jako vysoká priorita pro přeplánování.</span><span class="sxs-lookup"><span data-stu-id="536cf-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="536cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="536cf-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="536cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="536cf-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="536cf-106">[out] `true` Pokud se hostitel pokusí znovu naplánovat aktuální instanci úlohy, pokud je to možné, jinak `false` .</span><span class="sxs-lookup"><span data-stu-id="536cf-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="536cf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="536cf-107">Return Value</span></span>  
  
|<span data-ttu-id="536cf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="536cf-108">HRESULT</span></span>|<span data-ttu-id="536cf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="536cf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="536cf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="536cf-110">S_OK</span></span>|<span data-ttu-id="536cf-111">`NeedsPriorityRescheduling`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="536cf-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="536cf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="536cf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="536cf-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="536cf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="536cf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="536cf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="536cf-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="536cf-115">The call timed out.</span></span>|  
|<span data-ttu-id="536cf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="536cf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="536cf-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="536cf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="536cf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="536cf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="536cf-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="536cf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="536cf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="536cf-120">E_FAIL</span></span>|<span data-ttu-id="536cf-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="536cf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="536cf-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="536cf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="536cf-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="536cf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="536cf-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="536cf-124">Remarks</span></span>  
 <span data-ttu-id="536cf-125">V situacích, kdy je úloha blízko shromažďování systémem uvolňování paměti, CLR nastaví hodnotu `pbNeedsPriorityScheduling` na `true` , která indikuje přeplánování s vysokou prioritou.</span><span class="sxs-lookup"><span data-stu-id="536cf-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="536cf-126">Díky tomu může hostitel rychle naplánovat úlohu, což minimalizuje potenciální prodlevy v uvolňování paměti, a umožní hostiteli a modulu runtime spolupracovat při zachování prostředků paměti.</span><span class="sxs-lookup"><span data-stu-id="536cf-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="536cf-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="536cf-127">Requirements</span></span>  
 <span data-ttu-id="536cf-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="536cf-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="536cf-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="536cf-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="536cf-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="536cf-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="536cf-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="536cf-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536cf-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="536cf-132">See also</span></span>

- [<span data-ttu-id="536cf-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="536cf-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="536cf-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="536cf-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="536cf-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="536cf-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="536cf-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="536cf-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
