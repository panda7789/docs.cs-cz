---
title: ICorDebugFunction3::GetActiveReJitRequestILCode – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af101e8d842c20394816a3408c74709da941bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416179"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="183a9-102">ICorDebugFunction3::GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="183a9-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="183a9-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="183a9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="183a9-104">Získá ukazatele rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) obsahující IL z active ReJIT žádosti.</span><span class="sxs-lookup"><span data-stu-id="183a9-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183a9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="183a9-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="183a9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="183a9-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="183a9-107">Ukazatel na IL z active ReJIT žádosti.</span><span class="sxs-lookup"><span data-stu-id="183a9-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="183a9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="183a9-108">Remarks</span></span>  
 <span data-ttu-id="183a9-109">Pokud metodu reprezentovanou tímto objektem `ICorDebugFunction3` objekt má požadavek active ReJIT `ppReJitedILCode` vrací ukazatel na jeho IL.</span><span class="sxs-lookup"><span data-stu-id="183a9-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="183a9-110">Pokud neexistuje žádné aktivní požadavku, což je běžně, pak `ppReJitedILCode` je **null**.</span><span class="sxs-lookup"><span data-stu-id="183a9-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="183a9-111">Žádost o ReJIT stane aktivní jenom po provedení vrátí z [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) volání metody.</span><span class="sxs-lookup"><span data-stu-id="183a9-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="183a9-112">Ještě nemusí být kompilována a vláken může být stále provádí v původní verzi kód.</span><span class="sxs-lookup"><span data-stu-id="183a9-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="183a9-113">Během volání profileru se stane neaktivní žádost ReJIT [icorprofilerinfo4::requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="183a9-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="183a9-114">I po IL je vrátit zpět, vlákno můžete stále provádí v kódu překompilovat JIT (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="183a9-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="183a9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="183a9-115">Requirements</span></span>  
 <span data-ttu-id="183a9-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="183a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="183a9-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="183a9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="183a9-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="183a9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="183a9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="183a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183a9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="183a9-120">See Also</span></span>  
 [<span data-ttu-id="183a9-121">ICorDebugFunction3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="183a9-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [<span data-ttu-id="183a9-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="183a9-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="183a9-123">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="183a9-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
