---
title: "ICorDebugFunction3::GetActiveReJitRequestILCode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugFunction3.GetActiveReJitRequestILCode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6459297a2a04728ca87801bfc8484acec384a45c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="91bd8-102">ICorDebugFunction3::GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="91bd8-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="91bd8-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="91bd8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="91bd8-104">Získá ukazatele rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) obsahující IL z active ReJIT žádosti.</span><span class="sxs-lookup"><span data-stu-id="91bd8-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91bd8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91bd8-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91bd8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="91bd8-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="91bd8-107">Ukazatel na IL z active ReJIT žádosti.</span><span class="sxs-lookup"><span data-stu-id="91bd8-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91bd8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91bd8-108">Remarks</span></span>  
 <span data-ttu-id="91bd8-109">Pokud metodu reprezentovanou tímto objektem `ICorDebugFunction3` objekt má požadavek active ReJIT `ppReJitedILCode` vrací ukazatel na jeho IL.</span><span class="sxs-lookup"><span data-stu-id="91bd8-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="91bd8-110">Pokud neexistuje žádné aktivní požadavku, což je běžně, pak `ppReJitedILCode` je **null**.</span><span class="sxs-lookup"><span data-stu-id="91bd8-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="91bd8-111">Žádost o ReJIT stane aktivní jenom po provedení vrátí z [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) volání metody.</span><span class="sxs-lookup"><span data-stu-id="91bd8-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="91bd8-112">Ještě nemusí být kompilována a vláken může být stále provádí v původní verzi kód.</span><span class="sxs-lookup"><span data-stu-id="91bd8-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="91bd8-113">Během volání profileru se stane neaktivní žádost ReJIT [icorprofilerinfo4::requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="91bd8-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="91bd8-114">I po IL je vrátit zpět, vlákno můžete stále provádí v kódu překompilovat JIT (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="91bd8-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91bd8-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91bd8-115">Requirements</span></span>  
 <span data-ttu-id="91bd8-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91bd8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91bd8-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91bd8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91bd8-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91bd8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91bd8-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91bd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bd8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="91bd8-120">See Also</span></span>  
 [<span data-ttu-id="91bd8-121">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="91bd8-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [<span data-ttu-id="91bd8-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="91bd8-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="91bd8-123">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="91bd8-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
