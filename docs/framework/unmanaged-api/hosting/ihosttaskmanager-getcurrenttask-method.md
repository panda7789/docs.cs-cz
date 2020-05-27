---
title: IHostTaskManager::GetCurrentTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: 874951d6b5efed0dc08e6d0e166962767e295c3e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842046"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="5b34e-102">IHostTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="5b34e-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="5b34e-103">Získá ukazatel rozhraní na úlohu, která je aktuálně prováděna ve vlákně operačního systému, ze kterého je toto volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="5b34e-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b34e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b34e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b34e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b34e-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="5b34e-106">mimo Ukazatel na adresu instance [IHostTask](ihosttask-interface.md) , která představuje aktuálně spuštěnou úlohu nebo hodnotu null, pokud aktuálně není spuštěn žádný úkol.</span><span class="sxs-lookup"><span data-stu-id="5b34e-106">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b34e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5b34e-107">Return Value</span></span>  
  
|<span data-ttu-id="5b34e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b34e-108">HRESULT</span></span>|<span data-ttu-id="5b34e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5b34e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b34e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b34e-110">S_OK</span></span>|<span data-ttu-id="5b34e-111">`GetCurrentTask`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5b34e-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="5b34e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b34e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b34e-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5b34e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b34e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b34e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b34e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5b34e-115">The call timed out.</span></span>|  
|<span data-ttu-id="5b34e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b34e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b34e-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="5b34e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b34e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b34e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b34e-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="5b34e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b34e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b34e-120">E_FAIL</span></span>|<span data-ttu-id="5b34e-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="5b34e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b34e-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="5b34e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b34e-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5b34e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5b34e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="5b34e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="5b34e-125">`GetCurrentTask`bylo voláno v vlákně operačního systému mimo ovládací prvek hostitele.</span><span class="sxs-lookup"><span data-stu-id="5b34e-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b34e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b34e-126">Remarks</span></span>  
 <span data-ttu-id="5b34e-127">Hostitel může také nastavit `pTask` parametr na hodnotu null, aby se zabránilo úloze, kterou nezahájil vstup do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5b34e-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b34e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b34e-128">Requirements</span></span>  
 <span data-ttu-id="5b34e-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b34e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b34e-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b34e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b34e-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b34e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b34e-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b34e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b34e-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b34e-133">See also</span></span>

- [<span data-ttu-id="5b34e-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b34e-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5b34e-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b34e-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5b34e-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b34e-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5b34e-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b34e-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
