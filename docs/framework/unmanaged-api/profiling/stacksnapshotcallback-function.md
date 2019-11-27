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
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427076"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="73261-102">StackSnapshotCallback – funkce</span><span class="sxs-lookup"><span data-stu-id="73261-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="73261-103">Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="73261-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73261-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73261-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73261-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73261-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="73261-106">pro Pokud je tato hodnota nula, toto zpětné volání slouží pro spuštění nespravovaných snímků. v opačném případě je to identifikátor spravované funkce a toto zpětné volání je pro spravovaný rámec.</span><span class="sxs-lookup"><span data-stu-id="73261-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="73261-107">pro Hodnota ukazatele na instrukci nativního kódu v rámci.</span><span class="sxs-lookup"><span data-stu-id="73261-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="73261-108">pro Hodnota `COR_PRF_FRAME_INFO`, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73261-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="73261-109">Tato hodnota je platná pro použití pouze během tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="73261-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="73261-110">pro Velikost `CONTEXT` struktury, na kterou se odkazuje parametr `context`</span><span class="sxs-lookup"><span data-stu-id="73261-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="73261-111">pro Ukazatel na strukturu `CONTEXT` Win32, která představuje stav procesoru pro tento rámec.</span><span class="sxs-lookup"><span data-stu-id="73261-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="73261-112">Parametr `context` je platný pouze v případě, že byl předán příznak COR_PRF_SNAPSHOT_CONTEXT v `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="73261-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="73261-113">pro Ukazatel na data klienta, která jsou předána přímo z `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="73261-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73261-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73261-114">Remarks</span></span>  
 <span data-ttu-id="73261-115">Funkce `StackSnapshotCallback` je implementovaná modulem pro zápis profileru.</span><span class="sxs-lookup"><span data-stu-id="73261-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="73261-116">Je nutné omezit složitost práce v `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="73261-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="73261-117">Například při použití `ICorProfilerInfo2::DoStackSnapshot` asynchronním způsobem může cílové vlákno držet zámky.</span><span class="sxs-lookup"><span data-stu-id="73261-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="73261-118">Pokud kód v `StackSnapshotCallback` vyžaduje stejné zámky, může zablokování následovat.</span><span class="sxs-lookup"><span data-stu-id="73261-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="73261-119">Metoda `ICorProfilerInfo2::DoStackSnapshot` volá funkci `StackSnapshotCallback` jednou pro spravovaný rámec nebo jednou za spuštění nespravovaných snímků.</span><span class="sxs-lookup"><span data-stu-id="73261-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="73261-120">Pokud je zavolána `StackSnapshotCallback` pro spuštění nespravovaných snímků, profiler může použít kontext registrace (odkazovaná parametrem `context`) k provedení vlastního nespravovaného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73261-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="73261-121">V tomto případě struktura `CONTEXT` Win32 představuje stav procesoru pro poslední vloženou snímek v rámci spuštění nespravovaných snímků.</span><span class="sxs-lookup"><span data-stu-id="73261-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="73261-122">I když struktura `CONTEXT` Win32 zahrnuje hodnoty pro všechny Registry, měli byste spoléhat jenom na hodnoty registru ukazatelů zásobníku, registru ukazatelů na rámec, registru ukazatele na instrukce a na nestálé (tj. zachované) celočíselné registry.</span><span class="sxs-lookup"><span data-stu-id="73261-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73261-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73261-123">Requirements</span></span>  
 <span data-ttu-id="73261-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73261-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73261-125">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="73261-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="73261-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73261-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73261-127">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73261-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73261-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73261-128">See also</span></span>

- [<span data-ttu-id="73261-129">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="73261-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="73261-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="73261-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
