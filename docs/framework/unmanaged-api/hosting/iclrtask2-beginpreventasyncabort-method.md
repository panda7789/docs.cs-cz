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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a43fef7f6dfa6dbe0bb9f1c4caec2c9c224b93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763428"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="bde96-102">ICLRTask2::BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="bde96-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="bde96-103">Nové vlákno zpoždění přerušení žádosti z výsledkem přerušení vlákna v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="bde96-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bde96-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bde96-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bde96-105">Return Value</span></span>  
 <span data-ttu-id="bde96-106">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="bde96-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bde96-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bde96-107">HRESULT</span></span>|<span data-ttu-id="bde96-108">Popis</span><span class="sxs-lookup"><span data-stu-id="bde96-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bde96-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="bde96-109">S_OK</span></span>|<span data-ttu-id="bde96-110">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="bde96-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="bde96-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="bde96-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="bde96-112">Metoda byla volána pro vlákno, které není aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="bde96-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bde96-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bde96-113">Remarks</span></span>  
 <span data-ttu-id="bde96-114">Čítač přerušení podprocesu zpoždění pro aktuální vlákno voláním této metody zvýší o jedna.</span><span class="sxs-lookup"><span data-stu-id="bde96-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="bde96-115">Volání `BeginPreventAsyncAbort` a [iclrtask2::endpreventasyncabort –](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="bde96-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="bde96-116">Čítač je větší než nula, jsou zpožděné přerušení vlákna pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="bde96-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="bde96-117">Pokud se toto volání není spárovaný s volání `EndPreventAsyncAbort` metoda, je možné dosáhnout stavu, ve které vlákno nelze doručit přeruší aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="bde96-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="bde96-118">Prodleva není podporována pro vlákna je samotný přeruší.</span><span class="sxs-lookup"><span data-stu-id="bde96-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="bde96-119">Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM).</span><span class="sxs-lookup"><span data-stu-id="bde96-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="bde96-120">Nesprávné použití těchto metod může způsobit neurčené chování ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="bde96-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="bde96-121">Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač by mohl nastavit na nulu, když virtuální počítač má dříve zvýší jeho.</span><span class="sxs-lookup"><span data-stu-id="bde96-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="bde96-122">Podobně čítač interní nepovolenou přetečení.</span><span class="sxs-lookup"><span data-stu-id="bde96-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="bde96-123">Pokud překročí limit integrální vzhledem k tomu, že je zvýšen o hostitele a virtuální počítač, výsledné chování není zadána.</span><span class="sxs-lookup"><span data-stu-id="bde96-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde96-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bde96-124">Requirements</span></span>  
 <span data-ttu-id="bde96-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bde96-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde96-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bde96-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bde96-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bde96-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bde96-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde96-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde96-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bde96-129">See also</span></span>

- [<span data-ttu-id="bde96-130">EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="bde96-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="bde96-131">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bde96-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="bde96-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bde96-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bde96-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bde96-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bde96-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bde96-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="bde96-135">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="bde96-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
