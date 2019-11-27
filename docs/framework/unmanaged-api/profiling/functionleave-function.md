---
title: FunctionLeave – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 774a5d4e48f00ea8c28977f3f685dcd5a8da3199
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440583"
---
# <a name="functionleave-function"></a><span data-ttu-id="09c56-102">FunctionLeave – funkce</span><span class="sxs-lookup"><span data-stu-id="09c56-102">FunctionLeave Function</span></span>
<span data-ttu-id="09c56-103">Upozorní profileru, že se chystá návrat funkce k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="09c56-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09c56-104">Funkce `FunctionLeave` je v .NET Framework 2,0 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="09c56-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="09c56-105">Bude i nadále fungovat, ale dojde k snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="09c56-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="09c56-106">Místo toho použijte funkci [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="09c56-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c56-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09c56-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09c56-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="09c56-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="09c56-109">pro Identifikátor funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="09c56-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09c56-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09c56-110">Remarks</span></span>  
 <span data-ttu-id="09c56-111">Funkce `FunctionLeave` je zpětné volání; je nutné jej implementovat.</span><span class="sxs-lookup"><span data-stu-id="09c56-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="09c56-112">Implementace musí používat atribut třídy úložiště `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="09c56-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="09c56-113">Spouštěcí modul neuloží žádné Registry před voláním této funkce.</span><span class="sxs-lookup"><span data-stu-id="09c56-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="09c56-114">Při zadání je nutné uložit všechny používané Registry, včetně těch, které jsou v jednotce s plovoucí desetinnou čárkou (FPU).</span><span class="sxs-lookup"><span data-stu-id="09c56-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="09c56-115">Při ukončení je nutné obnovit zásobník odebráním všech parametrů, které byly vloženy volajícím.</span><span class="sxs-lookup"><span data-stu-id="09c56-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="09c56-116">Implementace `FunctionLeave` by neměla zablokovat, protože bude odloženo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="09c56-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="09c56-117">Implementace by se neměla pokoušet o uvolnění paměti, protože zásobník nemůže být ve stavu, který je k pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="09c56-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="09c56-118">V případě, že dojde k pokusu o uvolnění paměti, modul runtime zablokuje, dokud se `FunctionLeave` nevrátí.</span><span class="sxs-lookup"><span data-stu-id="09c56-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="09c56-119">Také funkce `FunctionLeave` nesmí volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="09c56-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09c56-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09c56-120">Requirements</span></span>  
 <span data-ttu-id="09c56-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09c56-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09c56-122">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="09c56-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="09c56-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09c56-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09c56-124">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="09c56-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c56-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09c56-125">See also</span></span>

- [<span data-ttu-id="09c56-126">FunctionEnter2 – funkce</span><span class="sxs-lookup"><span data-stu-id="09c56-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="09c56-127">FunctionLeave2 – funkce</span><span class="sxs-lookup"><span data-stu-id="09c56-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="09c56-128">FunctionTailcall2 – funkce</span><span class="sxs-lookup"><span data-stu-id="09c56-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="09c56-129">SetEnterLeaveFunctionHooks2 – metoda</span><span class="sxs-lookup"><span data-stu-id="09c56-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="09c56-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="09c56-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
