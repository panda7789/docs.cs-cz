---
title: IHostTask::SetCLRTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: b6eac134a4ffb1813cdc6957632ce5fb9b1a5fff
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842267"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="88f45-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="88f45-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="88f45-103">Přidruží `ICLRTask` instanci k aktuální instanci [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="88f45-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88f45-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88f45-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="88f45-106">pro Ukazatel rozhraní na `ICLRTask` instanci, která má být přidružena k aktuální `IHostTask` instanci.</span><span class="sxs-lookup"><span data-stu-id="88f45-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88f45-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="88f45-107">Return Value</span></span>  
  
|<span data-ttu-id="88f45-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88f45-108">HRESULT</span></span>|<span data-ttu-id="88f45-109">Popis</span><span class="sxs-lookup"><span data-stu-id="88f45-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88f45-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="88f45-110">S_OK</span></span>|<span data-ttu-id="88f45-111">`SetCLRTask`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="88f45-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="88f45-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88f45-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88f45-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="88f45-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88f45-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88f45-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88f45-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="88f45-115">The call timed out.</span></span>|  
|<span data-ttu-id="88f45-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88f45-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88f45-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="88f45-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88f45-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88f45-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88f45-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="88f45-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88f45-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88f45-120">E_FAIL</span></span>|<span data-ttu-id="88f45-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="88f45-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88f45-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="88f45-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88f45-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="88f45-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88f45-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88f45-124">Remarks</span></span>  
 <span data-ttu-id="88f45-125">Modul CLR volá `SetCLRTask` k přidružení `ICLRTask` instance k aktuální `IHostTask` instanci, která byla vytvořena voláním metody [IHostTaskManager:: CreateTask –](ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="88f45-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f45-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88f45-126">Requirements</span></span>  
 <span data-ttu-id="88f45-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88f45-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f45-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="88f45-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88f45-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88f45-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88f45-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f45-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f45-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="88f45-131">See also</span></span>

- [<span data-ttu-id="88f45-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88f45-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="88f45-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88f45-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="88f45-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88f45-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="88f45-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88f45-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
