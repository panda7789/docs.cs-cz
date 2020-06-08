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
ms.openlocfilehash: 8734fa9c9418b818cbe14ebe87ce2af6fa59c078
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499841"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="bb76c-102">ICorProfilerCallback::UnmanagedToManagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="bb76c-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="bb76c-103">Upozorní profileru, že došlo k přechodu z nespravovaného kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="bb76c-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb76c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb76c-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb76c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb76c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bb76c-106">pro ID volané funkce.</span><span class="sxs-lookup"><span data-stu-id="bb76c-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="bb76c-107">pro Hodnota výčtu [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , která určuje, zda došlo k přechodu z důvodu volání spravovaného kódu z nespravovaného kódu nebo z důvodu návratu z nespravované funkce volané spravovaném rozhraním.</span><span class="sxs-lookup"><span data-stu-id="bb76c-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb76c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb76c-108">Remarks</span></span>  
 <span data-ttu-id="bb76c-109">Pokud hodnota `reason` je COR_PRF_TRANSITION_RETURN a není `functionId` null, je ID funkce nespravované funkce a nikdy nebude zkompilována pomocí kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="bb76c-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="bb76c-110">Nespravované funkce mají přidružené základní informace, jako je název a některá metadata.</span><span class="sxs-lookup"><span data-stu-id="bb76c-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="bb76c-111">Pokud `reason` je hodnota COR_PRF_TRANSITION_CALL, může být možné, že volaná funkce (tj. spravovaná funkce) ještě nebyla kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="bb76c-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb76c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb76c-112">Requirements</span></span>  
 <span data-ttu-id="bb76c-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb76c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb76c-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bb76c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb76c-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bb76c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb76c-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb76c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb76c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb76c-117">See also</span></span>

- [<span data-ttu-id="bb76c-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb76c-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bb76c-119">ManagedToUnmanagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="bb76c-119">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="bb76c-120">Použití explicitního PInvoke v jazyce C++ (atribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="bb76c-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="bb76c-121">Použití zprostředkovatele komunikace C++ (implicitní PInvoke)</span><span class="sxs-lookup"><span data-stu-id="bb76c-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
