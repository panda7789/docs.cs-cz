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
ms.openlocfilehash: 69e3ecfc82985d52bd5b14e9faf2566e395b622b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124657"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="c8b0e-102">ICLRTask::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="c8b0e-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="c8b0e-103">Instruuje modul CLR (Common Language Runtime), aby přerušil úlohu reprezentovanou aktuální instancí [rozhraní ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) okamžitě a bezpodmínečně.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8b0e-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="c8b0e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8b0e-105">Return Value</span></span>  
  
|<span data-ttu-id="c8b0e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8b0e-106">HRESULT</span></span>|<span data-ttu-id="c8b0e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c8b0e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8b0e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8b0e-108">S_OK</span></span>|<span data-ttu-id="c8b0e-109">`RudeAbort` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="c8b0e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8b0e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8b0e-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8b0e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8b0e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8b0e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-113">The call timed out.</span></span>|  
|<span data-ttu-id="c8b0e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8b0e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8b0e-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8b0e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8b0e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8b0e-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8b0e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8b0e-118">E_FAIL</span></span>|<span data-ttu-id="c8b0e-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8b0e-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8b0e-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8b0e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8b0e-122">Remarks</span></span>  
 <span data-ttu-id="c8b0e-123">Hostitel volá `RudeAbort` k okamžitému přerušení úlohy.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="c8b0e-124">Není zaručeno provést finalizační metody a rutiny zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="c8b0e-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b0e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8b0e-125">Requirements</span></span>  
 <span data-ttu-id="c8b0e-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b0e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b0e-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c8b0e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8b0e-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c8b0e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8b0e-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b0e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b0e-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8b0e-130">See also</span></span>

- [<span data-ttu-id="c8b0e-131">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8b0e-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c8b0e-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8b0e-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c8b0e-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8b0e-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c8b0e-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8b0e-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
