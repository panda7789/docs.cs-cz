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
ms.openlocfilehash: cf6d84e483188ea7ed3376ba9b28906a38913fd4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124625"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="2f232-102">ICLRTask::SetTaskIdentifier – metoda</span><span class="sxs-lookup"><span data-stu-id="2f232-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="2f232-103">Instruuje modul CLR (Common Language Runtime), aby přidružil zadanou hodnotu identifikátoru k úloze reprezentované aktuální instancí [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2f232-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f232-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f232-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f232-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f232-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="2f232-106">pro Jedinečný identifikátor pro modul CLR (Common Language Runtime), který má být přidružen k úloze reprezentované aktuální instancí `ICLRTask`.</span><span class="sxs-lookup"><span data-stu-id="2f232-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f232-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f232-107">Return Value</span></span>  
  
|<span data-ttu-id="2f232-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f232-108">HRESULT</span></span>|<span data-ttu-id="2f232-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2f232-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f232-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f232-110">S_OK</span></span>|<span data-ttu-id="2f232-111">`SetTaskIdentifier` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2f232-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="2f232-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f232-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f232-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2f232-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f232-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f232-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f232-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2f232-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f232-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f232-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f232-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2f232-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f232-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f232-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f232-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2f232-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f232-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f232-120">E_FAIL</span></span>|<span data-ttu-id="2f232-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2f232-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f232-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2f232-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f232-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f232-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f232-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f232-124">Remarks</span></span>  
 <span data-ttu-id="2f232-125">Hostitel může přidružit identifikátor k úloze, aby bylo možné integrovat modul CLR a hostitele v ladicím prostředí.</span><span class="sxs-lookup"><span data-stu-id="2f232-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="2f232-126">Identifikátor nemá pro CLR žádný význam.</span><span class="sxs-lookup"><span data-stu-id="2f232-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="2f232-127">CLR je předá aplikaci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2f232-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="2f232-128">Ladicí program může tento identifikátor použít k přidružení zásobníku volání CLR k zásobníku volání hostitele a při zobrazení v uživatelském rozhraní ladicího programu povolit sjednocení příslušných trasovacích informací.</span><span class="sxs-lookup"><span data-stu-id="2f232-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f232-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f232-129">Requirements</span></span>  
 <span data-ttu-id="2f232-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f232-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f232-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f232-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f232-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f232-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f232-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f232-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f232-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f232-134">See also</span></span>

- [<span data-ttu-id="2f232-135">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f232-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2f232-136">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f232-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2f232-137">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f232-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2f232-138">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f232-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
