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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36947eb33460fe3f15cf4ade1cad55cb5e77f1cc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770226"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="90bc4-102">ICLRTask2::EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="90bc4-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="90bc4-103">Umožňuje nové nebo čekající vlákno přerušení požadavky na vlákno za následek přerušení v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="90bc4-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90bc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90bc4-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="90bc4-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90bc4-105">Return Value</span></span>  
 <span data-ttu-id="90bc4-106">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="90bc4-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90bc4-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90bc4-107">HRESULT</span></span>|<span data-ttu-id="90bc4-108">Popis</span><span class="sxs-lookup"><span data-stu-id="90bc4-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90bc4-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="90bc4-109">S_OK</span></span>|<span data-ttu-id="90bc4-110">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="90bc4-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="90bc4-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="90bc4-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="90bc4-112">Metoda byla volána pro vlákno, které není aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="90bc4-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90bc4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90bc4-113">Remarks</span></span>  
 <span data-ttu-id="90bc4-114">Volání čítač metoda sníží přerušení podprocesu zpoždění pro aktuální vlákno po druhém.</span><span class="sxs-lookup"><span data-stu-id="90bc4-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="90bc4-115">Volání [iclrtask2::beginpreventasyncabort –](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) a `EndPreventAsyncAbort` mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="90bc4-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="90bc4-116">Čítač je větší než nula, jsou zpožděné přerušení vlákna pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="90bc4-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="90bc4-117">Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM).</span><span class="sxs-lookup"><span data-stu-id="90bc4-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="90bc4-118">Nesprávné použití těchto metod může způsobit neurčené chování ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="90bc4-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="90bc4-119">Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač by mohl nastavit na nulu, když virtuální počítač má dříve zvýší jeho.</span><span class="sxs-lookup"><span data-stu-id="90bc4-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="90bc4-120">Podobně čítač interní nepovolenou přetečení.</span><span class="sxs-lookup"><span data-stu-id="90bc4-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="90bc4-121">Pokud překročí limit integrální vzhledem k tomu, že je zvýšen o hostitele a virtuální počítač, výsledné chování není zadána.</span><span class="sxs-lookup"><span data-stu-id="90bc4-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90bc4-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90bc4-122">Requirements</span></span>  
 <span data-ttu-id="90bc4-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90bc4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90bc4-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90bc4-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90bc4-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90bc4-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90bc4-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90bc4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90bc4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90bc4-127">See also</span></span>

- [<span data-ttu-id="90bc4-128">BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="90bc4-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="90bc4-129">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bc4-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="90bc4-130">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bc4-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="90bc4-131">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bc4-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="90bc4-132">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90bc4-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="90bc4-133">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="90bc4-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
