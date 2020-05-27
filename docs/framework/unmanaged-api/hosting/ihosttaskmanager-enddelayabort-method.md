---
title: IHostTaskManager::EndDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: 156626ce907c13987c0cca15016263291961037d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841968"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="a0471-102">IHostTaskManager::EndDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="a0471-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="a0471-103">Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přerušena, po předchozím volání metody [IHostTaskManager:: BeginDelayAbort –](ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="a0471-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0471-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0471-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a0471-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0471-105">Return Value</span></span>  
  
|<span data-ttu-id="a0471-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0471-106">HRESULT</span></span>|<span data-ttu-id="a0471-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a0471-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0471-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0471-108">S_OK</span></span>|<span data-ttu-id="a0471-109">`EndDelayAbort`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a0471-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="a0471-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0471-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0471-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a0471-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0471-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0471-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0471-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a0471-113">The call timed out.</span></span>|  
|<span data-ttu-id="a0471-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0471-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0471-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="a0471-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0471-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0471-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0471-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="a0471-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0471-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0471-118">E_FAIL</span></span>|<span data-ttu-id="a0471-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a0471-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0471-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a0471-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0471-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a0471-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a0471-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="a0471-122">E_UNEXPECTED</span></span>|<span data-ttu-id="a0471-123">`EndDelayAbort`byla volána bez odpovídajícího volání `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="a0471-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0471-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0471-124">Remarks</span></span>  
 <span data-ttu-id="a0471-125">Modul CLR provede odpovídající volání na `BeginDelayAbort` aktuální úkol před voláním `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="a0471-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="a0471-126">V případě absence takového volání by implementace [IHostTaskManager](ihosttaskmanager-interface.md) hostitele měla vrátit E_UNEXPECTED z `EndDelayAbort` a neměla by mít žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="a0471-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0471-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0471-127">Requirements</span></span>  
 <span data-ttu-id="a0471-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0471-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0471-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0471-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0471-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a0471-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0471-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0471-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0471-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0471-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="a0471-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0471-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a0471-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0471-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a0471-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0471-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a0471-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0471-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
