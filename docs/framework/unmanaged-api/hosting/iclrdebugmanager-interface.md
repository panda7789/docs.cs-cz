---
title: "ICLRDebugManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e537b955524f2721868ddf5da9fccf68f9d4efd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="fc773-102">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc773-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="fc773-103">Poskytuje metody, které umožňují hostitele k sadu úloh přidružit identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="fc773-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc773-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fc773-104">Methods</span></span>  
  
|<span data-ttu-id="fc773-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-105">Method</span></span>|<span data-ttu-id="fc773-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fc773-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc773-107">Beginconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="fc773-108">Vytvoří nové připojení mezi hostitelem a ladicí program pro přidružení úlohy s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="fc773-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="fc773-109">Endconnection – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="fc773-110">Odebere přidružení mezi seznamu úloh a identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="fc773-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="fc773-111">Getdacl – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="fc773-112">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="fc773-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="fc773-113">Isdebuggerattached – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="fc773-114">Získá hodnotu, která určuje, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="fc773-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="fc773-115">Setconnectiontasks – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="fc773-116">Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="fc773-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="fc773-117">Setdacl – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="fc773-118">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="fc773-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="fc773-119">Setsymbolreadingpolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="fc773-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="fc773-120">Nastavení zásad pro soubory databáze (PDB) program pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fc773-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="fc773-121">Zásady určuje, zda je informace o čísla řádků a soubory součástí zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="fc773-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc773-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc773-122">Remarks</span></span>  
 <span data-ttu-id="fc773-123">Při ladění scénáře, hostitel chtít úlohy skupiny podle vlastní programovací logiku.</span><span class="sxs-lookup"><span data-stu-id="fc773-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="fc773-124">Například seskupení by umožnilo vývojář zobrazit pouze úlohy, které vyžadují pomocí rozhraní API pro vývojáře, místo zobrazuje všechny úlohy spuštěné v procesu.</span><span class="sxs-lookup"><span data-stu-id="fc773-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="fc773-125">`ICLRDebugManager`Umožňuje na hostiteli a implementovat tento druh seskupení.</span><span class="sxs-lookup"><span data-stu-id="fc773-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fc773-126">Tři `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` a `EndConnection`, jsou závislé na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="fc773-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="fc773-127">Musí být voláno v uvedeném pořadí fungoval podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="fc773-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="fc773-128">Seskupení a identifikátory a popisné názvy, které hostitele přiřadí k seskupení, mít žádný význam pro modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="fc773-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="fc773-129">Modul CLR jenom předává informace podél ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fc773-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc773-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc773-130">Requirements</span></span>  
 <span data-ttu-id="fc773-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc773-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc773-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc773-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc773-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc773-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc773-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc773-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc773-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc773-135">See Also</span></span>  
 [<span data-ttu-id="fc773-136">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="fc773-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
