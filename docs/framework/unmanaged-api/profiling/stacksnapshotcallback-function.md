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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493978"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="6e418-102">StackSnapshotCallback – funkce</span><span class="sxs-lookup"><span data-stu-id="6e418-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="6e418-103">Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e418-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e418-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e418-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6e418-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e418-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="6e418-106">pro Pokud je tato hodnota nula, toto zpětné volání slouží pro spuštění nespravovaných snímků. v opačném případě je to identifikátor spravované funkce a toto zpětné volání je pro spravovaný rámec.</span><span class="sxs-lookup"><span data-stu-id="6e418-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="6e418-107">pro Hodnota ukazatele na instrukci nativního kódu v rámci.</span><span class="sxs-lookup"><span data-stu-id="6e418-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="6e418-108">pro `COR_PRF_FRAME_INFO`Hodnota, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6e418-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="6e418-109">Tato hodnota je platná pro použití pouze během tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6e418-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6e418-110">pro Velikost `CONTEXT` struktury, na kterou se odkazuje `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="6e418-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="6e418-111">pro Ukazatel na `CONTEXT` strukturu Win32, která představuje stav procesoru pro tento rámec.</span><span class="sxs-lookup"><span data-stu-id="6e418-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="6e418-112">`context`Parametr je platný pouze v případě, že byl předán příznak COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="6e418-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="6e418-113">pro Ukazatel na data klienta, která jsou předána přímo do z `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="6e418-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e418-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e418-114">Remarks</span></span>  
 <span data-ttu-id="6e418-115">`StackSnapshotCallback`Funkce je implementována modulem pro zápis profileru.</span><span class="sxs-lookup"><span data-stu-id="6e418-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="6e418-116">Je nutné omezit složitost práce, která byla dokončena v `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="6e418-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="6e418-117">Například při použití `ICorProfilerInfo2::DoStackSnapshot` asynchronním způsobem může cílové vlákno držet zámky.</span><span class="sxs-lookup"><span data-stu-id="6e418-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="6e418-118">Pokud kód v rámci `StackSnapshotCallback` vyžaduje stejné zámky, může zablokování následovat.</span><span class="sxs-lookup"><span data-stu-id="6e418-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="6e418-119">`ICorProfilerInfo2::DoStackSnapshot`Metoda volá `StackSnapshotCallback` funkci jednou pro každý spravovaný rámec nebo jednou za spuštění nespravovaných snímků.</span><span class="sxs-lookup"><span data-stu-id="6e418-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="6e418-120">Pokud `StackSnapshotCallback` je volána pro spuštění nespravovaných snímků, profiler může použít kontext registrace (odkazovaná `context` parametrem) k provedení vlastního nespravovaného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6e418-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="6e418-121">V tomto případě `CONTEXT` Struktura Win32 představuje stav procesoru pro poslední vloženou snímek v rámci spuštění nespravovaných snímků.</span><span class="sxs-lookup"><span data-stu-id="6e418-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="6e418-122">I když `CONTEXT` Struktura Win32 zahrnuje hodnoty pro všechny Registry, měli byste spoléhat jenom na hodnoty registru ukazatelů zásobníku, registru ukazatelů na rozhraní, registru ukazatelů na instrukce a na nestálé (tj., zachované) celočíselné registry.</span><span class="sxs-lookup"><span data-stu-id="6e418-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e418-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e418-123">Requirements</span></span>  
 <span data-ttu-id="6e418-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e418-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e418-125">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6e418-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6e418-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6e418-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e418-127">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e418-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e418-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e418-128">See also</span></span>

- [<span data-ttu-id="6e418-129">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="6e418-129">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="6e418-130">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="6e418-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
