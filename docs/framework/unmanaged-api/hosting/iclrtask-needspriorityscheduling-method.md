---
title: "ICLRTask::NeedsPriorityScheduling – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.NeedsPriorityScheduling
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ce57a4130c19ffd040bc9fbeba5e775a751efdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="b5b8b-102">ICLRTask::NeedsPriorityScheduling – metoda</span><span class="sxs-lookup"><span data-stu-id="b5b8b-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="b5b8b-103">Získá hodnotu, která určuje, zda aktuální úlohy, který je prvním out, musí být označen jako vysokou prioritu pro změnou plánu.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5b8b-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5b8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5b8b-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="b5b8b-106">[out] `true`, pokud se hostitel pokusí změnit plán naplánovaných aktuální instance úlohy co nejdříve; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5b8b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5b8b-107">Return Value</span></span>  
  
|<span data-ttu-id="b5b8b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5b8b-108">HRESULT</span></span>|<span data-ttu-id="b5b8b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b5b8b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5b8b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5b8b-110">S_OK</span></span>|<span data-ttu-id="b5b8b-111">`NeedsPriorityRescheduling`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="b5b8b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5b8b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5b8b-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5b8b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5b8b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5b8b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-115">The call timed out.</span></span>|  
|<span data-ttu-id="b5b8b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5b8b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5b8b-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5b8b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5b8b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5b8b-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5b8b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5b8b-120">E_FAIL</span></span>|<span data-ttu-id="b5b8b-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5b8b-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5b8b-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5b8b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5b8b-124">Remarks</span></span>  
 <span data-ttu-id="b5b8b-125">V situacích, kdy tato úloha je blízko shromažďovaných modulem garbage collector, modul CLR nastaví hodnotu `pbNeedsPriorityScheduling` k `true`, označující změnou plánu s vysokou prioritou.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="b5b8b-126">To umožňuje hostiteli, aby rychle změnit plán úlohy, a tím minimalizovat potenciální zpoždění při uvolňování paměti a povolení hostitele a modul runtime, aby spolupracovali při zachovávání paměťových prostředků.</span><span class="sxs-lookup"><span data-stu-id="b5b8b-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5b8b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5b8b-127">Requirements</span></span>  
 <span data-ttu-id="b5b8b-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5b8b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5b8b-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b5b8b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5b8b-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5b8b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5b8b-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5b8b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b8b-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5b8b-132">See Also</span></span>  
 [<span data-ttu-id="b5b8b-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5b8b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="b5b8b-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5b8b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b5b8b-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5b8b-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="b5b8b-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5b8b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
