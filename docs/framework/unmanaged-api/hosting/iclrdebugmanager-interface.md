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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d123177bf9f1b5eee1a2ba4d9b7f2042ddc07aa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434936"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="1eeda-102">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1eeda-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="1eeda-103">Poskytuje metody, které umožňují hostitele k sadu úloh přidružit identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="1eeda-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1eeda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1eeda-104">Methods</span></span>  
  
|<span data-ttu-id="1eeda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-105">Method</span></span>|<span data-ttu-id="1eeda-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1eeda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1eeda-107">BeginConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="1eeda-108">Vytvoří nové připojení mezi hostitelem a ladicí program pro přidružení úlohy s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="1eeda-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="1eeda-109">EndConnection – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="1eeda-110">Odebere přidružení mezi seznamu úloh a identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="1eeda-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="1eeda-111">GetDacl – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="1eeda-112">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="1eeda-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="1eeda-113">IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="1eeda-114">Získá hodnotu, která určuje, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="1eeda-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="1eeda-115">SetConnectionTasks – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="1eeda-116">Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.</span><span class="sxs-lookup"><span data-stu-id="1eeda-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="1eeda-117">SetDacl – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="1eeda-118">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="1eeda-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="1eeda-119">SetSymbolReadingPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="1eeda-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="1eeda-120">Nastavení zásad pro soubory databáze (PDB) program pro čtení.</span><span class="sxs-lookup"><span data-stu-id="1eeda-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="1eeda-121">Zásady určuje, zda je informace o čísla řádků a soubory součástí zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="1eeda-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eeda-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1eeda-122">Remarks</span></span>  
 <span data-ttu-id="1eeda-123">Při ladění scénáře, hostitel chtít úlohy skupiny podle vlastní programovací logiku.</span><span class="sxs-lookup"><span data-stu-id="1eeda-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="1eeda-124">Například seskupení by umožnilo vývojář zobrazit pouze úlohy, které vyžadují pomocí rozhraní API pro vývojáře, místo zobrazuje všechny úlohy spuštěné v procesu.</span><span class="sxs-lookup"><span data-stu-id="1eeda-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="1eeda-125">`ICLRDebugManager` Umožňuje na hostiteli a implementovat tento druh seskupení.</span><span class="sxs-lookup"><span data-stu-id="1eeda-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1eeda-126">Tři `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` a `EndConnection`, jsou závislé na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="1eeda-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="1eeda-127">Musí být voláno v uvedeném pořadí fungoval podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="1eeda-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="1eeda-128">Seskupení a identifikátory a popisné názvy, které hostitele přiřadí k seskupení, mít žádný význam pro modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="1eeda-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="1eeda-129">Modul CLR jenom předává informace podél ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1eeda-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eeda-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1eeda-130">Requirements</span></span>  
 <span data-ttu-id="1eeda-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eeda-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eeda-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1eeda-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1eeda-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1eeda-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1eeda-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eeda-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eeda-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="1eeda-135">See Also</span></span>  
 [<span data-ttu-id="1eeda-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="1eeda-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
