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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277e035ab542f895ca700ecd5f3205cc757c9ddd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769307"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="acb08-102">ICorProfilerCallback::ManagedToUnmanagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="acb08-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="acb08-103">Oznámí profileru, že došlo k přechodu ze spravovaného kódu do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="acb08-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acb08-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acb08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="acb08-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="acb08-106">[in] ID funkce, která je volána.</span><span class="sxs-lookup"><span data-stu-id="acb08-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="acb08-107">[in] Hodnota [cor_prf_transition_reason –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) výčet, který označuje, zda došlo k přechodu z důvodu volání nespravovaného kódu ze spravovaného kódu nebo z důvodu vrátit ze spravované funkce volány některý z nespravovaných.</span><span class="sxs-lookup"><span data-stu-id="acb08-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acb08-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acb08-108">Remarks</span></span>  
 <span data-ttu-id="acb08-109">Pokud hodnota `reason` je COR_PRF_TRANSITION_CALL, funkce ID je, že z nespravované funkce, které se nikdy již byly zkompilovány pomocí kompilátoru just-in-time.</span><span class="sxs-lookup"><span data-stu-id="acb08-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="acb08-110">Nespravované funkce mají základní informace související s nimi, jako jsou název a některá metadata.</span><span class="sxs-lookup"><span data-stu-id="acb08-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="acb08-111">Pokud nespravovaná funkce byla volána s použitím implicitního platformu vyvolání (PInvoke), modul runtime nemůže určit cílové volání a hodnota `functionId` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="acb08-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="acb08-112">Další informace o implicitní služba PInvoke, naleznete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="acb08-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb08-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acb08-113">Requirements</span></span>  
 <span data-ttu-id="acb08-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb08-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="acb08-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="acb08-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acb08-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acb08-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb08-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb08-118">See also</span></span>

- [<span data-ttu-id="acb08-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acb08-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="acb08-120">UnmanagedToManagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="acb08-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="acb08-121">Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="acb08-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
