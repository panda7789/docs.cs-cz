---
title: IHostTaskManager::EndThreadAffinity – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 2e857f951a837e1385d02dfc810fc12cfefd0d2b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841955"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="e5acd-102">IHostTaskManager::EndThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="e5acd-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="e5acd-103">Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přesunuta do jiného vlákna operačního systému za předchozích volání [IHostTaskManager:: BeginThreadAffinity –](ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5acd-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5acd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5acd-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e5acd-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5acd-105">Return Value</span></span>  
  
|<span data-ttu-id="e5acd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5acd-106">HRESULT</span></span>|<span data-ttu-id="e5acd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e5acd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5acd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5acd-108">S_OK</span></span>|<span data-ttu-id="e5acd-109">`EndThreadAffinity`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e5acd-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="e5acd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5acd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5acd-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e5acd-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5acd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5acd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5acd-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e5acd-113">The call timed out.</span></span>|  
|<span data-ttu-id="e5acd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5acd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5acd-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e5acd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5acd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5acd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5acd-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e5acd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5acd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5acd-118">E_FAIL</span></span>|<span data-ttu-id="e5acd-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e5acd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5acd-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e5acd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5acd-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e5acd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e5acd-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="e5acd-122">E_UNEXPECTED</span></span>|<span data-ttu-id="e5acd-123">`EndThreadAffinity`byla volána bez předchozího odpovídajícího volání metody `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="e5acd-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5acd-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5acd-124">Remarks</span></span>  
 <span data-ttu-id="e5acd-125">Modul CLR provede odpovídající volání na `BeginThreadAffinity` aktuální úkol před voláním `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="e5acd-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="e5acd-126">V případě absence takového volání by implementace [IHostTaskManager](ihosttaskmanager-interface.md) hostitele měla vrátit E_UNEXPECTED a Neprovádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="e5acd-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5acd-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5acd-127">Requirements</span></span>  
 <span data-ttu-id="e5acd-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5acd-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5acd-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e5acd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5acd-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e5acd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5acd-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5acd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5acd-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5acd-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="e5acd-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5acd-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e5acd-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5acd-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e5acd-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5acd-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e5acd-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5acd-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
