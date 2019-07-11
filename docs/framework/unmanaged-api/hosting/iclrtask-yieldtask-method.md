---
title: ICLRTask::YieldTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fde9586c1b3736b5db2c4814058dd23713dd34d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770332"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="aeb25-102">ICLRTask::YieldTask – metoda</span><span class="sxs-lookup"><span data-stu-id="aeb25-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="aeb25-103">Požadavky, že modul CLR (CLR) umístěny jste si poznamenali úkol, který aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje a zpřístupnit času procesoru pro jiné úlohy.</span><span class="sxs-lookup"><span data-stu-id="aeb25-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeb25-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aeb25-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aeb25-105">Return Value</span></span>  
  
|<span data-ttu-id="aeb25-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aeb25-106">HRESULT</span></span>|<span data-ttu-id="aeb25-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aeb25-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aeb25-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aeb25-108">S_OK</span></span>|<span data-ttu-id="aeb25-109">`YieldTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="aeb25-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="aeb25-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aeb25-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aeb25-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="aeb25-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aeb25-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aeb25-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aeb25-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="aeb25-113">The call timed out.</span></span>|  
|<span data-ttu-id="aeb25-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aeb25-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aeb25-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="aeb25-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aeb25-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aeb25-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aeb25-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="aeb25-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aeb25-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aeb25-118">E_FAIL</span></span>|<span data-ttu-id="aeb25-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="aeb25-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aeb25-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="aeb25-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aeb25-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aeb25-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb25-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aeb25-122">Remarks</span></span>  
 <span data-ttu-id="aeb25-123">Volá hostitele `YieldTask` pro požadavky na prostředky procesoru u jiných úloh nebo procesů.</span><span class="sxs-lookup"><span data-stu-id="aeb25-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="aeb25-124">Tato metoda je primárně určen pro umožnit dlouhotrvající kódu uvolňovat čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="aeb25-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="aeb25-125">Modul runtime pokusí vložit úkolu, který aktuální `ICLRTask` představuje instance ve stavu, kdy může přinést doba zpracování, ale je zaručeno úspěšné.</span><span class="sxs-lookup"><span data-stu-id="aeb25-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb25-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aeb25-126">Requirements</span></span>  
 <span data-ttu-id="aeb25-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb25-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb25-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeb25-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb25-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aeb25-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb25-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb25-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb25-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aeb25-131">See also</span></span>

- [<span data-ttu-id="aeb25-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeb25-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="aeb25-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeb25-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="aeb25-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeb25-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="aeb25-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeb25-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
