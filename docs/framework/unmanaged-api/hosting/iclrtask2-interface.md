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
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124528"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="1149d-102">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1149d-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="1149d-103">Poskytuje všechny funkce rozhraní [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ; Kromě toho poskytuje metody, které umožňují, aby bylo přerušení vlákna zpožděno v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1149d-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1149d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1149d-104">Methods</span></span>  
  
|<span data-ttu-id="1149d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1149d-105">Method</span></span>|<span data-ttu-id="1149d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1149d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1149d-107">BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="1149d-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="1149d-108">Zpozdí žádosti o přerušení nového vlákna v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1149d-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="1149d-109">EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="1149d-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="1149d-110">Umožňuje, aby nové nebo probíhající požadavky na přerušení vlákna byly výsledkem přerušení vlákna v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1149d-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1149d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1149d-111">Remarks</span></span>  
 <span data-ttu-id="1149d-112">Rozhraní `ICLRTask2` dědí `ICLRTask` rozhraní a přidává metody, které umožní hostiteli zpozdit přerušení vlákna, aby chránila oblast kódu, která nesmí selhat.</span><span class="sxs-lookup"><span data-stu-id="1149d-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="1149d-113">Volání `BeginPreventAsyncAbort` zvýší čítač zpožděného vlákna na přerušení pro aktuální vlákno a volání `EndPreventAsyncAbort` sníží.</span><span class="sxs-lookup"><span data-stu-id="1149d-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="1149d-114">Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="1149d-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="1149d-115">Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.</span><span class="sxs-lookup"><span data-stu-id="1149d-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="1149d-116">Pokud nejsou volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` spárována, je možné spojit se stavem, ve kterém je přerušeno přerušení vlákna nelze doručit do aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="1149d-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="1149d-117">Zpoždění se nerespektuje pro vlákno, které se přerušuje.</span><span class="sxs-lookup"><span data-stu-id="1149d-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="1149d-118">Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM).</span><span class="sxs-lookup"><span data-stu-id="1149d-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="1149d-119">Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="1149d-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="1149d-120">Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil.</span><span class="sxs-lookup"><span data-stu-id="1149d-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="1149d-121">Podobně není u vnitřního čítače přetečení kontrolováno.</span><span class="sxs-lookup"><span data-stu-id="1149d-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="1149d-122">Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.</span><span class="sxs-lookup"><span data-stu-id="1149d-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="1149d-123">Informace o členech zděděných z `ICLRTask` a o ostatních použití tohoto rozhraní naleznete v tématu rozhraní [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1149d-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1149d-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1149d-124">Requirements</span></span>  
 <span data-ttu-id="1149d-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1149d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1149d-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1149d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1149d-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1149d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1149d-128">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1149d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1149d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1149d-129">See also</span></span>

- [<span data-ttu-id="1149d-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1149d-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1149d-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1149d-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1149d-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1149d-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1149d-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1149d-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="1149d-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="1149d-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
