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
ms.openlocfilehash: b067ca72e030bce24a7efde5e3488a00024e9613
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762864"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="f22df-102">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f22df-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="f22df-103">Poskytuje všechny funkce rozhraní [ICLRTask](iclrtask-interface.md) ; Kromě toho poskytuje metody, které umožňují, aby bylo přerušení vlákna zpožděno v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="f22df-103">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f22df-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f22df-104">Methods</span></span>  
  
|<span data-ttu-id="f22df-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f22df-105">Method</span></span>|<span data-ttu-id="f22df-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f22df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f22df-107">BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="f22df-107">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="f22df-108">Zpozdí žádosti o přerušení nového vlákna v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="f22df-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="f22df-109">EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="f22df-109">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="f22df-110">Umožňuje, aby nové nebo probíhající požadavky na přerušení vlákna byly výsledkem přerušení vlákna v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="f22df-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f22df-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f22df-111">Remarks</span></span>  
 <span data-ttu-id="f22df-112">`ICLRTask2`Rozhraní dědí `ICLRTask` rozhraní a přidává metody, které umožní hostiteli zpozdit přerušení vlákna, aby chránila oblast kódu, která nesmí selhat.</span><span class="sxs-lookup"><span data-stu-id="f22df-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="f22df-113">Volání `BeginPreventAsyncAbort` zvýší čítač zpožděného vlákna na přerušení pro aktuální vlákno a zavoláním `EndPreventAsyncAbort` ho sníží.</span><span class="sxs-lookup"><span data-stu-id="f22df-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="f22df-114">Volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` můžou být vnořená.</span><span class="sxs-lookup"><span data-stu-id="f22df-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="f22df-115">Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.</span><span class="sxs-lookup"><span data-stu-id="f22df-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="f22df-116">Pokud volání `BeginPreventAsyncAbort` a `EndPreventAsyncAbort` nejsou spárována, je možné spojit se stavem, ve kterém nelze podprocesy přerušit, nelze doručit do aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="f22df-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="f22df-117">Zpoždění se nerespektuje pro vlákno, které se přerušuje.</span><span class="sxs-lookup"><span data-stu-id="f22df-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="f22df-118">Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM).</span><span class="sxs-lookup"><span data-stu-id="f22df-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="f22df-119">Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="f22df-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="f22df-120">Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil.</span><span class="sxs-lookup"><span data-stu-id="f22df-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="f22df-121">Podobně není u vnitřního čítače přetečení kontrolováno.</span><span class="sxs-lookup"><span data-stu-id="f22df-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="f22df-122">Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.</span><span class="sxs-lookup"><span data-stu-id="f22df-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="f22df-123">Informace o členech zděděných z `ICLRTask` a o ostatních použití tohoto rozhraní naleznete v rozhraní [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f22df-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f22df-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f22df-124">Requirements</span></span>  
 <span data-ttu-id="f22df-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f22df-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f22df-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f22df-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f22df-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f22df-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f22df-128">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f22df-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22df-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f22df-129">See also</span></span>

- [<span data-ttu-id="f22df-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f22df-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f22df-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f22df-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f22df-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f22df-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f22df-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f22df-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f22df-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f22df-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
