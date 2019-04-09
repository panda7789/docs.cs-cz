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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91c7235fb8790783b05b217cad755d8eedc88971
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092683"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="a68e1-102">ICLRTask::NeedsPriorityScheduling – metoda</span><span class="sxs-lookup"><span data-stu-id="a68e1-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="a68e1-103">Získá hodnotu určující, zda aktuální úloha, která je právě přepnutí, musí být označen jako s vysokou prioritou pro přeplánování.</span><span class="sxs-lookup"><span data-stu-id="a68e1-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a68e1-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a68e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a68e1-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="a68e1-106">[out] `true`v případě, že hostitel má pokusit o plánovanou zkoušku Přeplánovat aktuální instance úlohy, co nejdříve; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a68e1-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a68e1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a68e1-107">Return Value</span></span>  
  
|<span data-ttu-id="a68e1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a68e1-108">HRESULT</span></span>|<span data-ttu-id="a68e1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a68e1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a68e1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a68e1-110">S_OK</span></span>|`NeedsPriorityRescheduling` <span data-ttu-id="a68e1-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a68e1-111">returned successfully.</span></span>|  
|<span data-ttu-id="a68e1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a68e1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a68e1-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a68e1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a68e1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a68e1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a68e1-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a68e1-115">The call timed out.</span></span>|  
|<span data-ttu-id="a68e1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a68e1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a68e1-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a68e1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a68e1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a68e1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a68e1-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a68e1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a68e1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a68e1-120">E_FAIL</span></span>|<span data-ttu-id="a68e1-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a68e1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a68e1-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a68e1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a68e1-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a68e1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a68e1-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a68e1-124">Remarks</span></span>  
 <span data-ttu-id="a68e1-125">V situacích, ve kterém je úkol blízko shromažďují systémem uvolňování, modul CLR, nastaví hodnotu `pbNeedsPriorityScheduling` k `true`, určující nástroje přeplánování s vysokou prioritou.</span><span class="sxs-lookup"><span data-stu-id="a68e1-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="a68e1-126">To umožňuje hostiteli plánovanou zkoušku přeplánovat úloha rychle, a tím minimalizuje riziko zpožděním při uvolňování paměti a aktivace hostitele a modul runtime spolupracovat při zachování paměťových prostředků.</span><span class="sxs-lookup"><span data-stu-id="a68e1-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68e1-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a68e1-127">Requirements</span></span>  
 <span data-ttu-id="a68e1-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a68e1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68e1-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a68e1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a68e1-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a68e1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a68e1-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a68e1-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a68e1-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a68e1-132">See also</span></span>

- [<span data-ttu-id="a68e1-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a68e1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a68e1-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a68e1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a68e1-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a68e1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a68e1-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a68e1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
