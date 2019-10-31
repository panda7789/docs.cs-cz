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
ms.openlocfilehash: 43f2048c8ab85fa7e94f73aad430400ad4c8352f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124584"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="18c6c-102">ICLRTask::YieldTask – metoda</span><span class="sxs-lookup"><span data-stu-id="18c6c-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="18c6c-103">Požadavky, které modul CLR (Common Language Runtime) vyhradí úlohu, kterou aktuální instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) představuje, a nastavte čas procesoru k dispozici pro jiné úkoly.</span><span class="sxs-lookup"><span data-stu-id="18c6c-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18c6c-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="18c6c-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18c6c-105">Return Value</span></span>  
  
|<span data-ttu-id="18c6c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18c6c-106">HRESULT</span></span>|<span data-ttu-id="18c6c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="18c6c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18c6c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="18c6c-108">S_OK</span></span>|<span data-ttu-id="18c6c-109">`YieldTask` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="18c6c-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="18c6c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18c6c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18c6c-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="18c6c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18c6c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18c6c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18c6c-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="18c6c-113">The call timed out.</span></span>|  
|<span data-ttu-id="18c6c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18c6c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18c6c-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="18c6c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18c6c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18c6c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18c6c-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="18c6c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18c6c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18c6c-118">E_FAIL</span></span>|<span data-ttu-id="18c6c-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="18c6c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18c6c-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="18c6c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18c6c-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18c6c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18c6c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18c6c-122">Remarks</span></span>  
 <span data-ttu-id="18c6c-123">Hostitel volá `YieldTask` k vyžádání prostředků procesoru pro jiné úkoly nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="18c6c-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="18c6c-124">Tato metoda je primárně určena pro použití dlouhotrvajícího kódu k poskytnutí času procesoru.</span><span class="sxs-lookup"><span data-stu-id="18c6c-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="18c6c-125">Modul runtime se pokusí vložit úlohu, kterou aktuální `ICLRTask` instance představuje ve stavu, ve kterém může přinést čas zpracování, ale nezaručuje úspěch.</span><span class="sxs-lookup"><span data-stu-id="18c6c-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18c6c-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18c6c-126">Requirements</span></span>  
 <span data-ttu-id="18c6c-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18c6c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18c6c-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18c6c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18c6c-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18c6c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18c6c-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18c6c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c6c-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18c6c-131">See also</span></span>

- [<span data-ttu-id="18c6c-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18c6c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="18c6c-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18c6c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="18c6c-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18c6c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="18c6c-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18c6c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
