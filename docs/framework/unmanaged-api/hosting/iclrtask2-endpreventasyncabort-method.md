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
ms.openlocfilehash: 8fd48fbdc48672da4e2dfff83ddd11231877f519
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519707"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="4864c-102">ICLRTask2::EndPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="4864c-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="4864c-103">Umožňuje nové nebo čekající vlákno přerušení požadavky na vlákno za následek přerušení v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="4864c-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4864c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4864c-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4864c-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4864c-105">Return Value</span></span>  
 <span data-ttu-id="4864c-106">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="4864c-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4864c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4864c-107">HRESULT</span></span>|<span data-ttu-id="4864c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4864c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4864c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4864c-109">S_OK</span></span>|<span data-ttu-id="4864c-110">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="4864c-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="4864c-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="4864c-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="4864c-112">Metoda byla volána pro vlákno, které není aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="4864c-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4864c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4864c-113">Remarks</span></span>  
 <span data-ttu-id="4864c-114">Volání čítač metoda sníží přerušení podprocesu zpoždění pro aktuální vlákno po druhém.</span><span class="sxs-lookup"><span data-stu-id="4864c-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="4864c-115">Volání [iclrtask2::beginpreventasyncabort –](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) a `EndPreventAsyncAbort` mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="4864c-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="4864c-116">Čítač je větší než nula, jsou zpožděné přerušení vlákna pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="4864c-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="4864c-117">Funkce, který je zveřejněný prostřednictvím této funkce se používá interně pro virtuální počítač (VM).</span><span class="sxs-lookup"><span data-stu-id="4864c-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="4864c-118">Nesprávné použití těchto metod může způsobit neurčené chování ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="4864c-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="4864c-119">Například volání `EndPreventAsyncAbort` bez první volání `BeginPreventAsyncAbort` čítač by mohl nastavit na nulu, když virtuální počítač má dříve zvýší jeho.</span><span class="sxs-lookup"><span data-stu-id="4864c-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="4864c-120">Podobně čítač interní nepovolenou přetečení.</span><span class="sxs-lookup"><span data-stu-id="4864c-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="4864c-121">Pokud překročí limit integrální vzhledem k tomu, že je zvýšen o hostitele a virtuální počítač, výsledné chování není zadána.</span><span class="sxs-lookup"><span data-stu-id="4864c-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4864c-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4864c-122">Requirements</span></span>  
 <span data-ttu-id="4864c-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4864c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4864c-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4864c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4864c-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4864c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4864c-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4864c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4864c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4864c-127">See also</span></span>
- [<span data-ttu-id="4864c-128">BeginPreventAsyncAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="4864c-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="4864c-129">ICLRTask2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4864c-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="4864c-130">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4864c-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4864c-131">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4864c-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4864c-132">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4864c-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="4864c-133">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="4864c-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
