---
title: ICLRTask2::BeginPreventAsyncAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: 0da18c6850f393808d05dff8b1f19ac12b05bb86
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762887"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="21cd8-102">ICLRTask2::BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="21cd8-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="21cd8-103">Zpozdí žádosti o přerušení nových vláken z výsledku v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="21cd8-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21cd8-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="21cd8-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21cd8-105">Return Value</span></span>  
 <span data-ttu-id="21cd8-106">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="21cd8-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="21cd8-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21cd8-107">HRESULT</span></span>|<span data-ttu-id="21cd8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="21cd8-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21cd8-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="21cd8-109">S_OK</span></span>|<span data-ttu-id="21cd8-110">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="21cd8-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="21cd8-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="21cd8-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="21cd8-112">Metoda byla volána pro vlákno, které není aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="21cd8-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21cd8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21cd8-113">Remarks</span></span>  
 <span data-ttu-id="21cd8-114">Voláním této metody dojde k zvýšení počítadla zpožděného a přerušeného vlákna pro aktuální vlákno o jednu.</span><span class="sxs-lookup"><span data-stu-id="21cd8-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="21cd8-115">Volání `BeginPreventAsyncAbort` a [ICLRTask2:: EndPreventAsyncAbort –](iclrtask2-endpreventasyncabort-method.md) mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="21cd8-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="21cd8-116">Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.</span><span class="sxs-lookup"><span data-stu-id="21cd8-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="21cd8-117">Pokud toto volání není spárováno s voláním `EndPreventAsyncAbort` metody, je možné spojit stav, ve kterém nelze podprocesy přerušit, nelze doručit do aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="21cd8-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="21cd8-118">Zpoždění se nerespektuje pro vlákno, které se přerušuje.</span><span class="sxs-lookup"><span data-stu-id="21cd8-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="21cd8-119">Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM).</span><span class="sxs-lookup"><span data-stu-id="21cd8-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="21cd8-120">Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="21cd8-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="21cd8-121">Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil.</span><span class="sxs-lookup"><span data-stu-id="21cd8-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="21cd8-122">Podobně není u vnitřního čítače přetečení kontrolováno.</span><span class="sxs-lookup"><span data-stu-id="21cd8-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="21cd8-123">Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.</span><span class="sxs-lookup"><span data-stu-id="21cd8-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21cd8-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21cd8-124">Requirements</span></span>  
 <span data-ttu-id="21cd8-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cd8-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cd8-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21cd8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21cd8-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="21cd8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21cd8-128">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21cd8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cd8-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="21cd8-129">See also</span></span>

- [<span data-ttu-id="21cd8-130">EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="21cd8-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="21cd8-131">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21cd8-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="21cd8-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21cd8-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="21cd8-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21cd8-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="21cd8-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21cd8-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="21cd8-135">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="21cd8-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
