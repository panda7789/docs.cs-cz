---
title: ICorProfilerCallback::JITFunctionPitched – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71df3bc707099cbad06742d964881ee629216b69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782808"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="25223-102">ICorProfilerCallback::JITFunctionPitched – metoda</span><span class="sxs-lookup"><span data-stu-id="25223-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="25223-103">Oznámí profileru, který funkci, která byla just-in-time (JIT)-zkompilovány se odebral z paměti.</span><span class="sxs-lookup"><span data-stu-id="25223-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25223-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25223-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25223-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25223-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="25223-106">[in] ID funkce, které se odstranily.</span><span class="sxs-lookup"><span data-stu-id="25223-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25223-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25223-107">Remarks</span></span>  
 <span data-ttu-id="25223-108">Odebrané funkce je volána, profiler obdrží nové kompilace JIT události při nové kompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="25223-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="25223-109">V současné době kompilátor JIT společného jazyka runtime (CLR) neodebere funkce z paměti, tak tato zpětné volání se aktuálně nepoužívá a nebude přijímat pomocí profileru.</span><span class="sxs-lookup"><span data-stu-id="25223-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="25223-110">Hodnota `functionId` není platná, dokud je znovu zkompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="25223-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="25223-111">Při nové kompilaci funkci stejné `functionId` bude použita hodnota.</span><span class="sxs-lookup"><span data-stu-id="25223-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25223-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25223-112">Requirements</span></span>  
 <span data-ttu-id="25223-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25223-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25223-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25223-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25223-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25223-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25223-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25223-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25223-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25223-117">See also</span></span>

- [<span data-ttu-id="25223-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25223-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
