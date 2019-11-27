---
title: ICorProfilerCallback::ManagedToUnmanagedTransition – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: f4f5871bdd7adf11fcc811fd40c62e3027b8e607
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426185"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="d98bf-102">ICorProfilerCallback::ManagedToUnmanagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="d98bf-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="d98bf-103">Upozorní profileru, že došlo k přechodu ze spravovaného kódu do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d98bf-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d98bf-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d98bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d98bf-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d98bf-106">pro ID volané funkce.</span><span class="sxs-lookup"><span data-stu-id="d98bf-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="d98bf-107">pro Hodnota výčtu [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) , která určuje, zda došlo k přechodu z důvodu volání do nespravovaného kódu ze spravovaného kódu nebo z důvodu návratu ze spravované funkce volané nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="d98bf-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d98bf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d98bf-108">Remarks</span></span>  
 <span data-ttu-id="d98bf-109">Je-li hodnota `reason` COR_PRF_TRANSITION_CALL, ID funkce je taková, že se jedná o nespravovanou funkci, která nikdy nebyla zkompilována pomocí kompilátoru just-in-time.</span><span class="sxs-lookup"><span data-stu-id="d98bf-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="d98bf-110">K nespravovaným funkcím jsou přidružené základní informace, jako je název a některá metadata.</span><span class="sxs-lookup"><span data-stu-id="d98bf-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="d98bf-111">Pokud byla nespravovanou funkci volána pomocí implicitního vyvolání platformy (PInvoke), modul runtime nemůže určit cíl volání a hodnota `functionId` bude null.</span><span class="sxs-lookup"><span data-stu-id="d98bf-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="d98bf-112">Další informace o implicitním PInvoke naleznete v [tématu C++ using Interop (implicitní PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="d98bf-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98bf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d98bf-113">Requirements</span></span>  
 <span data-ttu-id="d98bf-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d98bf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98bf-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d98bf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d98bf-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d98bf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d98bf-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98bf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98bf-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d98bf-118">See also</span></span>

- [<span data-ttu-id="d98bf-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d98bf-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d98bf-120">UnmanagedToManagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="d98bf-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="d98bf-121">Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="d98bf-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
