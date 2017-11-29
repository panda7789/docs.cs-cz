---
title: "ICLRTask2::EndPreventAsyncAbort – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2.EndPreventAsyncAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c76a75004b4593e8e93aa4dd999c85c0fb7cf38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="32bdc-102">ICLRTask2::EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="32bdc-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="32bdc-103">Umožňuje nové nebo nevyřízené žádosti o zrušení vláken za následek vlákno zruší na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="32bdc-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32bdc-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="32bdc-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32bdc-105">Return Value</span></span>  
 <span data-ttu-id="32bdc-106">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="32bdc-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="32bdc-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32bdc-107">HRESULT</span></span>|<span data-ttu-id="32bdc-108">Popis</span><span class="sxs-lookup"><span data-stu-id="32bdc-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32bdc-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="32bdc-109">S_OK</span></span>|<span data-ttu-id="32bdc-110">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="32bdc-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="32bdc-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="32bdc-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="32bdc-112">Volání metody na vlákno, která není aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="32bdc-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32bdc-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32bdc-113">Remarks</span></span>  
 <span data-ttu-id="32bdc-114">Tento čítač snižuje přerušení podprocesu zpoždění metoda volání pro aktuální vlákno o jednu.</span><span class="sxs-lookup"><span data-stu-id="32bdc-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="32bdc-115">Volání [iclrtask2::beginpreventasyncabort –](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) a `EndPreventAsyncAbort` mohou být použity.</span><span class="sxs-lookup"><span data-stu-id="32bdc-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="32bdc-116">Tak dlouho, dokud hodnota čítače je větší než nula, jsou odložené přerušení přístup z více vláken pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="32bdc-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="32bdc-117">Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM).</span><span class="sxs-lookup"><span data-stu-id="32bdc-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="32bdc-118">Zneužití z těchto metod může způsobit neurčené chování ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="32bdc-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="32bdc-119">Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač může nastavit na hodnotu nula, pokud virtuální počítač má dříve se zvýší.</span><span class="sxs-lookup"><span data-stu-id="32bdc-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="32bdc-120">Podobně není čítač interní kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="32bdc-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="32bdc-121">Pokud překročí limitu integrální vzhledem k tomu, že se zvýší o hostitel a virtuální počítač, neurčené jejich výsledné chování.</span><span class="sxs-lookup"><span data-stu-id="32bdc-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32bdc-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32bdc-122">Requirements</span></span>  
 <span data-ttu-id="32bdc-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32bdc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bdc-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32bdc-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32bdc-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32bdc-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32bdc-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bdc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bdc-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="32bdc-127">See Also</span></span>  
 [<span data-ttu-id="32bdc-128">Beginpreventasyncabort – metoda</span><span class="sxs-lookup"><span data-stu-id="32bdc-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)  
 [<span data-ttu-id="32bdc-129">Iclrtask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32bdc-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="32bdc-130">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32bdc-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="32bdc-131">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32bdc-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="32bdc-132">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32bdc-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="32bdc-133">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="32bdc-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
