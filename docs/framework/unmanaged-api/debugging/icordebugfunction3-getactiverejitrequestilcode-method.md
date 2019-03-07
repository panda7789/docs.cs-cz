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
ms.openlocfilehash: 90c93b87265bb806914c5e503a6702dd1d563bc0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471861"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="6e971-102">ICorDebugFunction3::GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="6e971-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="6e971-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="6e971-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6e971-104">Získá ukazatel rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , který obsahuje IL z aktivního ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="6e971-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e971-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e971-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e971-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e971-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="6e971-107">Ukazatel do IL z aktivního ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="6e971-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e971-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e971-108">Remarks</span></span>  
 <span data-ttu-id="6e971-109">Pokud metoda představovaného tímto rozhraním `ICorDebugFunction3` objekt má aktivní požadavek ReJIT `ppReJitedILCode` vrací ukazatel na jeho IL.</span><span class="sxs-lookup"><span data-stu-id="6e971-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="6e971-110">Pokud neexistuje žádný aktivní požadavek případ je běžný, pak `ppReJitedILCode` je **null**.</span><span class="sxs-lookup"><span data-stu-id="6e971-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="6e971-111">Žádost o ReJIT stane aktivním hned po spuštění se vrátí z [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) volání metody.</span><span class="sxs-lookup"><span data-stu-id="6e971-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="6e971-112">Ještě nemusí být JIT kompilován a vláken může být stále provádí v původní verzi kódu.</span><span class="sxs-lookup"><span data-stu-id="6e971-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="6e971-113">Žádost o ReJIT přestane být aktivní během volání profileru [icorprofilerinfo4::requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6e971-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="6e971-114">I když se vrátí zpět IL, vlákno může stále provádí v kódu překompilován JIT (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="6e971-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e971-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e971-115">Requirements</span></span>  
 <span data-ttu-id="6e971-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e971-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e971-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e971-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e971-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e971-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e971-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e971-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e971-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e971-120">See also</span></span>
- [<span data-ttu-id="6e971-121">ICorDebugFunction3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e971-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="6e971-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6e971-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6e971-123">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="6e971-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
