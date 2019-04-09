---
title: ICLRTask2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172468"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="59ffd-102">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ffd-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="59ffd-103">Obsahuje všechny funkce, které jsou součástí [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní; navíc poskytuje metody, které umožňují zrušení vláken k zpozdit u aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="59ffd-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59ffd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59ffd-104">Methods</span></span>  
  
|<span data-ttu-id="59ffd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59ffd-105">Method</span></span>|<span data-ttu-id="59ffd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="59ffd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59ffd-107">BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="59ffd-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="59ffd-108">Nové vlákno zpoždění přerušit požadavky pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="59ffd-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="59ffd-109">EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="59ffd-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="59ffd-110">Umožňuje nové nebo čekající vlákno přerušení požadavky na vlákno za následek přerušení v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="59ffd-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ffd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59ffd-111">Remarks</span></span>  
 <span data-ttu-id="59ffd-112">`ICLRTask2` Dědí rozhraní `ICLRTask` rozhraní a přidá metody, které umožňují hostitele tak, aby zpoždění přerušení vlákna, k ochraně oblasti kódu, který nesmí nezdaří.</span><span class="sxs-lookup"><span data-stu-id="59ffd-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="59ffd-113">Volání `BeginPreventAsyncAbort` zvýší čítač přerušení podprocesu zpoždění pro aktuální vlákno a volání `EndPreventAsyncAbort` sníží ho.</span><span class="sxs-lookup"><span data-stu-id="59ffd-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="59ffd-114">Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="59ffd-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="59ffd-115">Čítač je větší než nula, jsou zpožděné přerušení vlákna pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="59ffd-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="59ffd-116">Pokud volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` jsou nespárováno, je možné dosáhnout stavu, ve které vlákno nelze doručit přeruší aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="59ffd-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="59ffd-117">Prodleva není podporována pro vlákna je samotný přeruší.</span><span class="sxs-lookup"><span data-stu-id="59ffd-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="59ffd-118">Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM).</span><span class="sxs-lookup"><span data-stu-id="59ffd-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="59ffd-119">Nesprávné použití těchto metod může způsobit neurčené chování ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="59ffd-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="59ffd-120">Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač by mohl nastavit na nulu, když virtuální počítač má dříve zvýší jeho.</span><span class="sxs-lookup"><span data-stu-id="59ffd-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="59ffd-121">Podobně čítač interní nepovolenou přetečení.</span><span class="sxs-lookup"><span data-stu-id="59ffd-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="59ffd-122">Pokud překročí limit integrální vzhledem k tomu, že je zvýšen o hostitele a virtuální počítač, výsledné chování není zadána.</span><span class="sxs-lookup"><span data-stu-id="59ffd-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="59ffd-123">Pro informace o členy zděděné z `ICLRTask` a o dalších použitích tohoto rozhraní, podívejte se [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="59ffd-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ffd-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59ffd-124">Requirements</span></span>  
 <span data-ttu-id="59ffd-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ffd-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ffd-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59ffd-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59ffd-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59ffd-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="59ffd-128">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="59ffd-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59ffd-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59ffd-129">See also</span></span>

- [<span data-ttu-id="59ffd-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ffd-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="59ffd-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ffd-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="59ffd-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ffd-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="59ffd-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ffd-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="59ffd-134">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="59ffd-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
