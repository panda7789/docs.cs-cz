---
title: ICLRDebugManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 008143c608cd19bee9dd115e97620906fb5b93b9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129410"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="e2550-102">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2550-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="e2550-103">Poskytuje metody, které umožňují hostiteli přidružit sadu úkolů s identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="e2550-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2550-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2550-104">Methods</span></span>  
  
|<span data-ttu-id="e2550-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-105">Method</span></span>|<span data-ttu-id="e2550-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e2550-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2550-107">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="e2550-108">Vytvoří nové propojení mezi hostitelem a ladicím programem k přidružení úkolů k identifikátoru a popisnému názvu.</span><span class="sxs-lookup"><span data-stu-id="e2550-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="e2550-109">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="e2550-110">Odebere přidružení mezi seznamem úkolů a identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="e2550-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="e2550-111">GetDacl – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="e2550-112">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="e2550-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="e2550-113">IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="e2550-114">Získá hodnotu, která označuje, zda je k procesu připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="e2550-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="e2550-115">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="e2550-116">Přidruží seznam instancí [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) s identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="e2550-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="e2550-117">SetDacl – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="e2550-118">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="e2550-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="e2550-119">SetSymbolReadingPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="e2550-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="e2550-120">Nastaví zásadu pro soubory databáze programu pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e2550-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="e2550-121">Tato zásada určuje, zda jsou do zásobníků volání zahrnuty informace o číslech řádků a souborech.</span><span class="sxs-lookup"><span data-stu-id="e2550-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2550-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2550-122">Remarks</span></span>  
 <span data-ttu-id="e2550-123">Ve scénářích ladění může hostitel chtít seskupit úkoly podle vlastní programovací logiky.</span><span class="sxs-lookup"><span data-stu-id="e2550-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="e2550-124">Například seskupení umožní vývojářům zobrazit jenom úkoly požadované rozhraními API vývojářů místo zobrazení všech úloh spuštěných v procesu.</span><span class="sxs-lookup"><span data-stu-id="e2550-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="e2550-125">`ICLRDebugManager` umožňuje hostiteli implementovat tento druh seskupení.</span><span class="sxs-lookup"><span data-stu-id="e2550-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2550-126">Tři `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` a `EndConnection`, jsou závislé na sobě.</span><span class="sxs-lookup"><span data-stu-id="e2550-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="e2550-127">Musí být volány v daném pořadí, aby fungovaly podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="e2550-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="e2550-128">Seskupení a identifikátory a popisné názvy, které hostitel přiřadí seskupení, nemají žádný význam pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="e2550-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="e2550-129">Modul CLR pouze předává informace spolu s ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="e2550-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2550-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2550-130">Requirements</span></span>  
 <span data-ttu-id="e2550-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2550-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2550-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e2550-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2550-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e2550-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2550-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2550-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2550-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2550-135">See also</span></span>

- [<span data-ttu-id="e2550-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="e2550-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
