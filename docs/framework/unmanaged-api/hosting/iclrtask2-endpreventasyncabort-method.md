---
title: ICLRTask2::EndPreventAsyncAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 3ea36c56ef9ccf5886ba96191627e5283da186f7
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762849"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="5362f-102">ICLRTask2::EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="5362f-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="5362f-103">Umožňuje, aby nové nebo probíhající požadavky na přerušení vlákna byly výsledkem přerušení vlákna v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="5362f-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5362f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5362f-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5362f-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5362f-105">Return Value</span></span>  
 <span data-ttu-id="5362f-106">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="5362f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5362f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5362f-107">HRESULT</span></span>|<span data-ttu-id="5362f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5362f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5362f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="5362f-109">S_OK</span></span>|<span data-ttu-id="5362f-110">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5362f-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="5362f-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="5362f-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="5362f-112">Metoda byla volána pro vlákno, které není aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="5362f-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5362f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5362f-113">Remarks</span></span>  
 <span data-ttu-id="5362f-114">Voláním této metody dojde k snížení čítače zpoždění-vlákno-přerušení pro aktuální vlákno o jednu.</span><span class="sxs-lookup"><span data-stu-id="5362f-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="5362f-115">Volání [ICLRTask2:: BeginPreventAsyncAbort –](iclrtask2-beginpreventasyncabort-method.md) a `EndPreventAsyncAbort` mohou být vnořena.</span><span class="sxs-lookup"><span data-stu-id="5362f-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="5362f-116">Dokud je čítač větší než nula, přerušení vlákna pro aktuální vlákno jsou zpožděna.</span><span class="sxs-lookup"><span data-stu-id="5362f-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="5362f-117">Funkce, která je vystavena touto funkcí, je interně používána virtuálním počítačem (VM).</span><span class="sxs-lookup"><span data-stu-id="5362f-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="5362f-118">Zneužití těchto metod může způsobit nespecifikované chování virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="5362f-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="5362f-119">Například volání `EndPreventAsyncAbort` bez prvního volání `BeginPreventAsyncAbort` může nastavit čítač na hodnotu nula, pokud ho virtuální počítač dříve přizpůsobil.</span><span class="sxs-lookup"><span data-stu-id="5362f-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="5362f-120">Podobně není u vnitřního čítače přetečení kontrolováno.</span><span class="sxs-lookup"><span data-stu-id="5362f-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="5362f-121">Pokud překročí svůj integrální limit, protože se zvyšuje od hostitele i virtuálního počítače, výsledné chování není určeno.</span><span class="sxs-lookup"><span data-stu-id="5362f-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5362f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5362f-122">Requirements</span></span>  
 <span data-ttu-id="5362f-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5362f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5362f-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5362f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5362f-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5362f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5362f-126">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5362f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5362f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="5362f-127">See also</span></span>

- [<span data-ttu-id="5362f-128">BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="5362f-128">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="5362f-129">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5362f-129">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="5362f-130">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5362f-130">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5362f-131">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5362f-131">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5362f-132">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5362f-132">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5362f-133">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5362f-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
