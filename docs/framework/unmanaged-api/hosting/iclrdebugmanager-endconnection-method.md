---
title: ICLRDebugManager::EndConnection – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: d3d081e389e29833f24063ba75289f3db8c5504a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504274"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="af38d-102">ICLRDebugManager::EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="af38d-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="af38d-103">Odebere přidružení mezi seznamem úkolů a identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="af38d-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af38d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af38d-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af38d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af38d-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="af38d-106">pro Identifikátor konkrétního hostitele pro připojení a přidružený seznam úloh modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="af38d-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af38d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af38d-107">Return Value</span></span>  
  
|<span data-ttu-id="af38d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af38d-108">HRESULT</span></span>|<span data-ttu-id="af38d-109">Description</span><span class="sxs-lookup"><span data-stu-id="af38d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af38d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="af38d-110">S_OK</span></span>|<span data-ttu-id="af38d-111">`EndConnection`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="af38d-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="af38d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af38d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af38d-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="af38d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af38d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af38d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af38d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="af38d-115">The call timed out.</span></span>|  
|<span data-ttu-id="af38d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af38d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af38d-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="af38d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af38d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af38d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af38d-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="af38d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af38d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af38d-120">E_FAIL</span></span>|<span data-ttu-id="af38d-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="af38d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af38d-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="af38d-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af38d-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="af38d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="af38d-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="af38d-124">E_INVALIDARG</span></span>|<span data-ttu-id="af38d-125">[BeginConnection –](iclrdebugmanager-beginconnection-method.md) se nikdy nevolal pomocí `dwConnectionId` nebo `dwConnectionId` byl nulový.</span><span class="sxs-lookup"><span data-stu-id="af38d-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af38d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af38d-126">Remarks</span></span>  
 <span data-ttu-id="af38d-127">[ICLRDebugManager](iclrdebugmanager-interface.md) poskytuje tři metody, `BeginConnection` , [SetConnectionTasks –](iclrdebugmanager-setconnectiontasks-method.md)a `EndConnection` , pro přiřazování seznamů úkolů s identifikátory a popisnými názvy.</span><span class="sxs-lookup"><span data-stu-id="af38d-127">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="af38d-128">Tyto tři metody musí být volány v určitém pořadí pro každou sadu úkolů.</span><span class="sxs-lookup"><span data-stu-id="af38d-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="af38d-129">`BeginConnection`se označuje jako první, aby se navázalo nové připojení.</span><span class="sxs-lookup"><span data-stu-id="af38d-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="af38d-130">`SetConnectionTasks`se volá vedle a poskytne sadu úloh, které se mají přidružit k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="af38d-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="af38d-131">`EndConnection`je volána jako poslední k odebrání přidružení mezi seznamem úkolů a identifikátorem a popisným názvem. Volání různých připojení však mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="af38d-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af38d-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af38d-132">Requirements</span></span>  
 <span data-ttu-id="af38d-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af38d-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af38d-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af38d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af38d-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af38d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af38d-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af38d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af38d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af38d-137">See also</span></span>

- [<span data-ttu-id="af38d-138">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af38d-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="af38d-139">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af38d-139">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="af38d-140">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="af38d-140">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="af38d-141">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="af38d-141">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="af38d-142">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af38d-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
