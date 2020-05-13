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
ms.openlocfilehash: 9e7f682752cfefae63b574655a4fc5e8964146a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213176"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="5a3c9-102">ICorDebugFunction3::GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="5a3c9-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="5a3c9-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="5a3c9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5a3c9-104">Získá ukazatel rozhraní na [ICorDebugILCode](icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5a3c9-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3c9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a3c9-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a3c9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a3c9-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="5a3c9-107">Ukazatel na IL z aktivní žádosti ReJIT</span><span class="sxs-lookup"><span data-stu-id="5a3c9-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a3c9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a3c9-108">Remarks</span></span>  
 <span data-ttu-id="5a3c9-109">Pokud metoda reprezentovaná tímto `ICorDebugFunction3` objektem má aktivní požadavek ReJIT, `ppReJitedILCode` vrátí ukazatel na jeho Il.</span><span class="sxs-lookup"><span data-stu-id="5a3c9-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="5a3c9-110">Pokud neexistuje žádná aktivní žádost, což je běžný případ, `ppReJitedILCode` je **hodnota null**.</span><span class="sxs-lookup"><span data-stu-id="5a3c9-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="5a3c9-111">Žádost ReJIT se aktivuje hned po návratu spuštění z volání metody [ICorProfilerCallback4:: GetReJITParameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5a3c9-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="5a3c9-112">Ještě nemusí být zkompilován kompilátorem JIT a vlákna mohou být stále spuštěna v původní verzi kódu.</span><span class="sxs-lookup"><span data-stu-id="5a3c9-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="5a3c9-113">Požadavek ReJIT se v průběhu volání profileru do metody [ICorProfilerInfo4:: RequestRevert –](../profiling/icorprofilerinfo4-requestrevert-method.md) přestanou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="5a3c9-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="5a3c9-114">I po vrácení IL se může vlákno i nadále spouštět v kódu ReJIT (JIT rekompilovaná).</span><span class="sxs-lookup"><span data-stu-id="5a3c9-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3c9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a3c9-115">Requirements</span></span>  
 <span data-ttu-id="5a3c9-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3c9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3c9-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a3c9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a3c9-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5a3c9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a3c9-119">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a3c9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3c9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a3c9-120">See also</span></span>

- [<span data-ttu-id="5a3c9-121">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="5a3c9-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="5a3c9-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a3c9-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5a3c9-123">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="5a3c9-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
