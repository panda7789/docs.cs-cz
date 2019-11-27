---
title: FunctionTailcall – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: c83a55a74542d94559b50b89ef784de0bd55d0db
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427343"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="3915b-102">FunctionTailcall – funkce</span><span class="sxs-lookup"><span data-stu-id="3915b-102">FunctionTailcall Function</span></span>
<span data-ttu-id="3915b-103">Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="3915b-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3915b-104">Funkce `FunctionTailcall` je v .NET Framework verze 2,0 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3915b-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3915b-105">Bude i nadále fungovat, ale dojde k snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="3915b-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="3915b-106">Místo toho použijte funkci [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3915b-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3915b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3915b-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3915b-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="3915b-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="3915b-109">pro Identifikátor aktuálně vykonávané funkce, která má být volána pro volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="3915b-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3915b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3915b-110">Remarks</span></span>  
 <span data-ttu-id="3915b-111">Cílová funkce volání Tail bude používat aktuální rámec zásobníku a vrátí se přímo volajícímu funkce, která provedla volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="3915b-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="3915b-112">To znamená, že zpětné volání [FunctionLeave –](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) nebude vystaveno pro funkci, která je cílem volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="3915b-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="3915b-113">Funkce `FunctionTailcall` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="3915b-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="3915b-114">Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="3915b-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3915b-115">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="3915b-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3915b-116">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="3915b-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3915b-117">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="3915b-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3915b-118">Implementace `FunctionTailcall` by neměla zablokovat, protože bude odloženo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3915b-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3915b-119">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3915b-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3915b-120">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionTailcall` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="3915b-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="3915b-121">Také funkce `FunctionTailcall` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="3915b-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3915b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3915b-122">Requirements</span></span>  
 <span data-ttu-id="3915b-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3915b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3915b-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="3915b-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3915b-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3915b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3915b-126">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3915b-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3915b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3915b-127">See also</span></span>

- [<span data-ttu-id="3915b-128">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3915b-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="3915b-129">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="3915b-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="3915b-130">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3915b-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3915b-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3915b-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
