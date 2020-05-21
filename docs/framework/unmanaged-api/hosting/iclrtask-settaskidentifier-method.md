---
title: ICLRTask::SetTaskIdentifier – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: e1b93356fd40aacdec2e764946e3e3b12d0bd306
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762939"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="548f7-102">ICLRTask::SetTaskIdentifier – metoda</span><span class="sxs-lookup"><span data-stu-id="548f7-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="548f7-103">Instruuje modul CLR (Common Language Runtime), aby přidružil zadanou hodnotu identifikátoru k úloze reprezentované aktuální instancí [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="548f7-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="548f7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="548f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="548f7-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="548f7-106">pro Jedinečný identifikátor pro modul CLR (Common Language Runtime), který se má přidružit k úloze reprezentované aktuální `ICLRTask` instancí.</span><span class="sxs-lookup"><span data-stu-id="548f7-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="548f7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="548f7-107">Return Value</span></span>  
  
|<span data-ttu-id="548f7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="548f7-108">HRESULT</span></span>|<span data-ttu-id="548f7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="548f7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="548f7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="548f7-110">S_OK</span></span>|<span data-ttu-id="548f7-111">`SetTaskIdentifier`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="548f7-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="548f7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="548f7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="548f7-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="548f7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="548f7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="548f7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="548f7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="548f7-115">The call timed out.</span></span>|  
|<span data-ttu-id="548f7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="548f7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="548f7-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="548f7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="548f7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="548f7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="548f7-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="548f7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="548f7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="548f7-120">E_FAIL</span></span>|<span data-ttu-id="548f7-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="548f7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="548f7-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="548f7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="548f7-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="548f7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="548f7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="548f7-124">Remarks</span></span>  
 <span data-ttu-id="548f7-125">Hostitel může přidružit identifikátor k úloze, aby bylo možné integrovat modul CLR a hostitele v ladicím prostředí.</span><span class="sxs-lookup"><span data-stu-id="548f7-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="548f7-126">Identifikátor nemá pro CLR žádný význam.</span><span class="sxs-lookup"><span data-stu-id="548f7-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="548f7-127">CLR je předá aplikaci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="548f7-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="548f7-128">Ladicí program může tento identifikátor použít k přidružení zásobníku volání CLR k zásobníku volání hostitele a při zobrazení v uživatelském rozhraní ladicího programu povolit sjednocení příslušných trasovacích informací.</span><span class="sxs-lookup"><span data-stu-id="548f7-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548f7-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="548f7-129">Requirements</span></span>  
 <span data-ttu-id="548f7-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="548f7-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="548f7-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="548f7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="548f7-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="548f7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="548f7-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="548f7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548f7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="548f7-134">See also</span></span>

- [<span data-ttu-id="548f7-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548f7-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="548f7-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548f7-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="548f7-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548f7-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="548f7-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="548f7-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
