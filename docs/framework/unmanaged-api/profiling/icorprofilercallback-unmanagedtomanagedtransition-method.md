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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 312f133c263becfd815f1b4ad48dff4892963aaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227844"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="bbfeb-102">ICorProfilerCallback::UnmanagedToManagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="bbfeb-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="bbfeb-103">Oznámí profileru, že došlo k přechodu z nespravovaného kódu pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="bbfeb-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbfeb-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbfeb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbfeb-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bbfeb-106">[in] ID funkce, která je volána.</span><span class="sxs-lookup"><span data-stu-id="bbfeb-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="bbfeb-107">[in] Hodnota [cor_prf_transition_reason –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) výčet, který označuje, zda došlo k přechodu z důvodu volání do spravovaného kódu z nespravovaného kódu nebo z důvodu návrat z nespravované funkce volá spravovaný ten.</span><span class="sxs-lookup"><span data-stu-id="bbfeb-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbfeb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbfeb-108">Remarks</span></span>  
 <span data-ttu-id="bbfeb-109">Pokud hodnota `reason` je COR_PRF_TRANSITION_RETURN a `functionId` není null, funkce ID je, že z nespravované funkce a se nikdy již byly zkompilovány pomocí kompilátoru just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="bbfeb-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="bbfeb-110">Nespravované funkce mají některé základní informace související s nimi, jako jsou název a některá metadata.</span><span class="sxs-lookup"><span data-stu-id="bbfeb-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="bbfeb-111">Pokud hodnota `reason` COR_PRF_TRANSITION_CALL, je to možné, že volaná funkce (to znamená, spravované funkce) ještě nebyla kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="bbfeb-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfeb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbfeb-112">Requirements</span></span>  
 <span data-ttu-id="bbfeb-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbfeb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfeb-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bbfeb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bbfeb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbfeb-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bbfeb-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bbfeb-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbfeb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbfeb-117">See also</span></span>

- [<span data-ttu-id="bbfeb-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbfeb-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bbfeb-119">ManagedToUnmanagedTransition – metoda</span><span class="sxs-lookup"><span data-stu-id="bbfeb-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="bbfeb-120">Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="bbfeb-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="bbfeb-121">Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)</span><span class="sxs-lookup"><span data-stu-id="bbfeb-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
