---
title: StackSnapshotCallback – funkce
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e71696282a3c9e6d25793b583ee19f306e167b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486235"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="7b988-102">StackSnapshotCallback – funkce</span><span class="sxs-lookup"><span data-stu-id="7b988-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="7b988-103">Poskytuje informace o každý spravovaný rámec a každé spuštění nespravované rámce v zásobníku během procházení zásobníku, která inicializuje profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7b988-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b988-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b988-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b988-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b988-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="7b988-106">[in] Pokud tato hodnota je nula, je tato zpětné volání pro spuštění nespravované snímky. v opačném případě je to identifikátor spravované funkce a je tato zpětné volání pro spravovaný rámec.</span><span class="sxs-lookup"><span data-stu-id="7b988-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="7b988-107">[in] Hodnota ukazatele na instrukci nativního kódu v rámci.</span><span class="sxs-lookup"><span data-stu-id="7b988-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="7b988-108">[in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b988-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="7b988-109">Tato hodnota je platná pro použití pouze během tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7b988-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7b988-110">[in] Velikost `CONTEXT` strukturu, která odkazuje `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="7b988-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="7b988-111">[in] Ukazatel na Win32 `CONTEXT` struktura, která představuje stav procesoru pro tento rámec.</span><span class="sxs-lookup"><span data-stu-id="7b988-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="7b988-112">`context` Parametr je platný jenom v případě, že byla předána příznak COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="7b988-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="7b988-113">[in] Ukazatel na data klienta, který se předává přímo z `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="7b988-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b988-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b988-114">Remarks</span></span>  
 <span data-ttu-id="7b988-115">`StackSnapshotCallback` Funkce je implementováno tvůrci profileru.</span><span class="sxs-lookup"><span data-stu-id="7b988-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="7b988-116">Je třeba omezit složitost práci v `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="7b988-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="7b988-117">Například při použití `ICorProfilerInfo2::DoStackSnapshot` v asynchronním režimu cílové vlákno může být zámky.</span><span class="sxs-lookup"><span data-stu-id="7b988-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="7b988-118">Pokud kódu v rámci `StackSnapshotCallback` vyžaduje stejné uzamčení, zablokování může následovat.</span><span class="sxs-lookup"><span data-stu-id="7b988-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="7b988-119">`ICorProfilerInfo2::DoStackSnapshot` Volání metod `StackSnapshotCallback` funkce jednou pro každý spravovaný snímek nebo jednou za běhu nespravované snímků.</span><span class="sxs-lookup"><span data-stu-id="7b988-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="7b988-120">Pokud `StackSnapshotCallback` je volána pro spuštění nespravované snímků, profiler může použít kontext registr (odkazuje `context` parametr) provádět vlastní nespravovaná zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b988-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="7b988-121">V takovém případě Win32 `CONTEXT` struktura představuje stav procesoru pro nedávno vložené rámce v rámci běhu nespravované snímků.</span><span class="sxs-lookup"><span data-stu-id="7b988-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="7b988-122">I když Win32 `CONTEXT` struktura obsahuje hodnoty pro všechny registrů, by se neměla spoléhat jenom na hodnoty registru ukazatel zásobníku, registr ukazatelů rámce, registr ukazatele instrukcí a stálé (který se zachovají) celočíselné registry.</span><span class="sxs-lookup"><span data-stu-id="7b988-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b988-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b988-123">Requirements</span></span>  
 <span data-ttu-id="7b988-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b988-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b988-125">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7b988-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7b988-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b988-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b988-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b988-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b988-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b988-128">See also</span></span>
- [<span data-ttu-id="7b988-129">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="7b988-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="7b988-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7b988-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
