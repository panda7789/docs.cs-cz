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
ms.openlocfilehash: 70a55b833acb7fa946c694a63e1e8b51562938bc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777728"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="b6920-102">ICorDebugFunction3::GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="b6920-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="b6920-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="b6920-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b6920-104">Získá ukazatel rozhraní na [ICorDebugILCode](icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.</span><span class="sxs-lookup"><span data-stu-id="b6920-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6920-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6920-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6920-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6920-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="b6920-107">Ukazatel na IL z aktivní žádosti ReJIT</span><span class="sxs-lookup"><span data-stu-id="b6920-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6920-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6920-108">Remarks</span></span>  
 <span data-ttu-id="b6920-109">Pokud metoda reprezentovaná tímto objektem `ICorDebugFunction3` má aktivní požadavek ReJIT, `ppReJitedILCode` vrátí ukazatel na jeho IL.</span><span class="sxs-lookup"><span data-stu-id="b6920-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="b6920-110">Pokud není žádná aktivní žádost, což je běžný případ, `ppReJitedILCode` je **null**.</span><span class="sxs-lookup"><span data-stu-id="b6920-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="b6920-111">Žádost ReJIT se aktivuje hned po návratu spuštění z volání metody [ICorProfilerCallback4:: GetReJITParameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6920-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="b6920-112">Ještě nemusí být zkompilován kompilátorem JIT a vlákna mohou být stále spuštěna v původní verzi kódu.</span><span class="sxs-lookup"><span data-stu-id="b6920-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="b6920-113">Požadavek ReJIT se v průběhu volání profileru do metody [ICorProfilerInfo4:: RequestRevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) přestanou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="b6920-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="b6920-114">I po vrácení IL se může vlákno i nadále spouštět v kódu ReJIT (JIT rekompilovaná).</span><span class="sxs-lookup"><span data-stu-id="b6920-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6920-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6920-115">Requirements</span></span>  
 <span data-ttu-id="b6920-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6920-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6920-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6920-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6920-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6920-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6920-119">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6920-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6920-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6920-120">See also</span></span>

- [<span data-ttu-id="b6920-121">ICorDebugFunction3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6920-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="b6920-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b6920-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b6920-123">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="b6920-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
