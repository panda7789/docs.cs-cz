---
title: ICLRTask::SwitchOut – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 75517ae55ebae07242f19c19c5473780ce4b0809
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762913"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="f35bc-102">ICLRTask::SwitchOut – metoda</span><span class="sxs-lookup"><span data-stu-id="f35bc-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="f35bc-103">Upozorní modul CLR (Common Language Runtime) na to, že úloha reprezentovaná aktuální instancí [ICLRTask](iclrtask-interface.md) již není v funkčním stavu.</span><span class="sxs-lookup"><span data-stu-id="f35bc-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f35bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f35bc-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f35bc-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f35bc-105">Return Value</span></span>  
  
|<span data-ttu-id="f35bc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f35bc-106">HRESULT</span></span>|<span data-ttu-id="f35bc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f35bc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f35bc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f35bc-108">S_OK</span></span>|<span data-ttu-id="f35bc-109">`SwitchOut`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f35bc-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="f35bc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f35bc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f35bc-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f35bc-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f35bc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f35bc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f35bc-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f35bc-113">The call timed out.</span></span>|  
|<span data-ttu-id="f35bc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f35bc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f35bc-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f35bc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f35bc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f35bc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f35bc-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f35bc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f35bc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f35bc-118">E_FAIL</span></span>|<span data-ttu-id="f35bc-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f35bc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f35bc-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f35bc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f35bc-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f35bc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f35bc-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f35bc-122">Remarks</span></span>  
 <span data-ttu-id="f35bc-123">Hostitel volá `SwitchOut` , aby INFORMOVAL CLR o tom, že dočasně zastavil provádění úlohy, kterou představuje aktuální `ICLRTask` instance, a úlohu znovu naplánuje.</span><span class="sxs-lookup"><span data-stu-id="f35bc-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f35bc-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f35bc-124">Requirements</span></span>  
 <span data-ttu-id="f35bc-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f35bc-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f35bc-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f35bc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f35bc-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f35bc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f35bc-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f35bc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35bc-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f35bc-129">See also</span></span>

- [<span data-ttu-id="f35bc-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f35bc-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f35bc-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f35bc-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f35bc-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f35bc-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f35bc-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f35bc-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
