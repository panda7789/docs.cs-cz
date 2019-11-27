---
title: ICorProfilerCallback::UnmanagedToManagedTransition – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439890"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="05bf9-102">ICorProfilerCallback::UnmanagedToManagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="05bf9-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="05bf9-103">Upozorní profileru, že došlo k přechodu z nespravovaného kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="05bf9-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05bf9-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05bf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05bf9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="05bf9-106">pro ID volané funkce.</span><span class="sxs-lookup"><span data-stu-id="05bf9-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="05bf9-107">pro Hodnota výčtu [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) , která určuje, zda došlo k přechodu z důvodu volání spravovaného kódu z nespravovaného kódu nebo z důvodu návratu z nespravované funkce volané spravovaném rozhraním.</span><span class="sxs-lookup"><span data-stu-id="05bf9-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05bf9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05bf9-108">Remarks</span></span>  
 <span data-ttu-id="05bf9-109">Pokud je hodnota `reason` COR_PRF_TRANSITION_RETURN a `functionId` není null, je ID funkce nespravované funkce a nikdy nebude zkompilována pomocí kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="05bf9-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="05bf9-110">Nespravované funkce mají přidružené základní informace, jako je název a některá metadata.</span><span class="sxs-lookup"><span data-stu-id="05bf9-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="05bf9-111">Pokud je hodnota `reason` COR_PRF_TRANSITION_CALL, může být možné, že volaná funkce (tj. spravovaná funkce) ještě nebyla kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="05bf9-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05bf9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05bf9-112">Requirements</span></span>  
 <span data-ttu-id="05bf9-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05bf9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05bf9-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05bf9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05bf9-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05bf9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05bf9-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05bf9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bf9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05bf9-117">See also</span></span>

- [<span data-ttu-id="05bf9-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05bf9-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="05bf9-119">ManagedToUnmanagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="05bf9-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="05bf9-120">Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="05bf9-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="05bf9-121">Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)</span><span class="sxs-lookup"><span data-stu-id="05bf9-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
