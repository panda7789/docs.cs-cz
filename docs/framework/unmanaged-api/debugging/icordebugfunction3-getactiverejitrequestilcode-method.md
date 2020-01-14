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
ms.openlocfilehash: 53fedde028c7551e929cb583d38a4ec6937f2a8c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938097"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="93d89-102">ICorDebugFunction3::GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="93d89-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="93d89-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="93d89-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="93d89-104">Získá ukazatel rozhraní na [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.</span><span class="sxs-lookup"><span data-stu-id="93d89-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d89-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93d89-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93d89-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="93d89-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="93d89-107">Ukazatel na IL z aktivní žádosti ReJIT</span><span class="sxs-lookup"><span data-stu-id="93d89-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93d89-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93d89-108">Remarks</span></span>  
 <span data-ttu-id="93d89-109">Pokud metoda reprezentovaná tímto objektem `ICorDebugFunction3` má aktivní požadavek ReJIT, `ppReJitedILCode` vrátí ukazatel na jeho IL.</span><span class="sxs-lookup"><span data-stu-id="93d89-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="93d89-110">Pokud není žádná aktivní žádost, což je běžný případ, `ppReJitedILCode` je **null**.</span><span class="sxs-lookup"><span data-stu-id="93d89-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="93d89-111">Žádost ReJIT se aktivuje hned po návratu spuštění z volání metody [ICorProfilerCallback4:: GetReJITParameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93d89-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="93d89-112">Ještě nemusí být zkompilován kompilátorem JIT a vlákna mohou být stále spuštěna v původní verzi kódu.</span><span class="sxs-lookup"><span data-stu-id="93d89-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="93d89-113">Požadavek ReJIT se v průběhu volání profileru do metody [ICorProfilerInfo4:: RequestRevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) přestanou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="93d89-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="93d89-114">I po vrácení IL se může vlákno i nadále spouštět v kódu ReJIT (JIT rekompilovaná).</span><span class="sxs-lookup"><span data-stu-id="93d89-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d89-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93d89-115">Requirements</span></span>  
 <span data-ttu-id="93d89-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93d89-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d89-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93d89-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93d89-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93d89-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93d89-119">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d89-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d89-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93d89-120">See also</span></span>

- [<span data-ttu-id="93d89-121">ICorDebugFunction3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93d89-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="93d89-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="93d89-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="93d89-123">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="93d89-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
