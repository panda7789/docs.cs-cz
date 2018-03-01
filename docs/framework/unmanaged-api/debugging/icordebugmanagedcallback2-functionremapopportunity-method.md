---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 208803acea65b24429938dc646e7abe70949b237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="5fc0a-102">ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda</span><span class="sxs-lookup"><span data-stu-id="5fc0a-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="5fc0a-103">Upozorní ladicí program, že provádění kódu dosáhl bod sekvence ve starší verzi upravená funkce.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fc0a-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fc0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fc0a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5fc0a-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující upravená funkce.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5fc0a-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, na kterém byl zjištěn bod přemapování přerušení.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="5fc0a-108">[v] Ukazatel na ICorDebugFunction objekt, který představuje verzi funkce, která aktuálně běží ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="5fc0a-109">[v] Ukazatel na ICorDebugFunction objekt, který představuje nejnovější verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="5fc0a-110">[v] Posun (MSIL intermediate language) Microsoft ukazatel instrukce v předchozí verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fc0a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fc0a-111">Remarks</span></span>  
 <span data-ttu-id="5fc0a-112">Tato zpětného volání umožní ladicího programu přemapovat ukazatel instrukce na správné místo v nové verzi zadaná funkce voláním [icordebugilframe2::remapfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="5fc0a-113">Pokud ladicí program nevyvolá `RemapFunction` před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda, modul runtime budou i nadále spouštět původní kód a bude platit jiné `FunctionRemapOpportunity` zpětného volání na další bod sekvence.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="5fc0a-114">Pro každý rámce, který spouští starší verzi danou funkci dokud ladicí program vrátí S_OK bude volána tento zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5fc0a-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc0a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fc0a-115">Requirements</span></span>  
 <span data-ttu-id="5fc0a-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fc0a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc0a-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fc0a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fc0a-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fc0a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fc0a-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc0a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fc0a-120">See Also</span></span>  
 [<span data-ttu-id="5fc0a-121">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fc0a-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="5fc0a-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fc0a-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
