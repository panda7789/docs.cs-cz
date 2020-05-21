---
title: ICLRTask::RudeAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 5d6e19fe307373c2920fd60b04bff482b238c5c4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762952"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="e406f-102">ICLRTask::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="e406f-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="e406f-103">Instruuje modul CLR (Common Language Runtime), aby přerušil úlohu reprezentovanou aktuální instancí [rozhraní ICLRTask](iclrtask-interface.md) okamžitě a bezpodmínečně.</span><span class="sxs-lookup"><span data-stu-id="e406f-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e406f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e406f-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="e406f-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e406f-105">Return Value</span></span>  
  
|<span data-ttu-id="e406f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e406f-106">HRESULT</span></span>|<span data-ttu-id="e406f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e406f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e406f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e406f-108">S_OK</span></span>|<span data-ttu-id="e406f-109">`RudeAbort`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e406f-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="e406f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e406f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e406f-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e406f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e406f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e406f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e406f-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e406f-113">The call timed out.</span></span>|  
|<span data-ttu-id="e406f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e406f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e406f-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e406f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e406f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e406f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e406f-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e406f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e406f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e406f-118">E_FAIL</span></span>|<span data-ttu-id="e406f-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e406f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e406f-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e406f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e406f-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e406f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e406f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e406f-122">Remarks</span></span>  
 <span data-ttu-id="e406f-123">Hostitel volá `RudeAbort` okamžité přerušení úlohy.</span><span class="sxs-lookup"><span data-stu-id="e406f-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="e406f-124">Není zaručeno provést finalizační metody a rutiny zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="e406f-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e406f-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e406f-125">Requirements</span></span>  
 <span data-ttu-id="e406f-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e406f-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e406f-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e406f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e406f-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e406f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e406f-129">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e406f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e406f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e406f-130">See also</span></span>

- [<span data-ttu-id="e406f-131">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e406f-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e406f-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e406f-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e406f-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e406f-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e406f-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e406f-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
