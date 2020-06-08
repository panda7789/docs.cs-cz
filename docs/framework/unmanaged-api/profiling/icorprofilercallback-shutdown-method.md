---
title: ICorProfilerCallback::Shutdown – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: f6873de1a864489d144a671b1a9e1349eaf77d15
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503176"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="977f9-102">ICorProfilerCallback::Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="977f9-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="977f9-103">Oznamuje profileru, že se aplikace vypíná.</span><span class="sxs-lookup"><span data-stu-id="977f9-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="977f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="977f9-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="977f9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="977f9-105">Remarks</span></span>  
 <span data-ttu-id="977f9-106">Kód profileru nemůže bezpečně volat metody rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) po `Shutdown` volání metody.</span><span class="sxs-lookup"><span data-stu-id="977f9-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="977f9-107">Jakákoli volání `ICorProfilerInfo` metod způsobí nedefinované chování poté, co `Shutdown` Metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="977f9-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="977f9-108">K určitým neměnným událostem může docházet i po vypnutí. Profiler by měl být při výskytu okamžitě vrácen.</span><span class="sxs-lookup"><span data-stu-id="977f9-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="977f9-109">`Shutdown`Metoda bude volána pouze v případě, že je spravovaná aplikace, která je profilovaná, spuštěna jako spravovaný kód (to znamená, že počáteční rámec v zásobníku procesu je spravovaný).</span><span class="sxs-lookup"><span data-stu-id="977f9-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="977f9-110">Pokud se aplikace spustila jako nespravovaný kód, ale později se přeskočí do spravovaného kódu, vytvoří se instance modulu CLR (Common Language Runtime), pak `Shutdown` se nebude volat.</span><span class="sxs-lookup"><span data-stu-id="977f9-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="977f9-111">V těchto případech by měl Profiler do knihovny zahrnout `DllMain` rutinu, která používá hodnotu DLL_PROCESS_DETACH k uvolnění prostředků a k vyčištění zpracování dat, jako je například vyprazdňování trasování na disk a tak dále.</span><span class="sxs-lookup"><span data-stu-id="977f9-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="977f9-112">Obecně platí, že Profiler se musí vypořádat s neočekávanými vypnutími.</span><span class="sxs-lookup"><span data-stu-id="977f9-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="977f9-113">Například proces může být zastaven `TerminateProcess` metodou Win32's (deklarovaným v Winbase. h).</span><span class="sxs-lookup"><span data-stu-id="977f9-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="977f9-114">V ostatních případech CLR zachová určitá spravovaná vlákna (vlákna na pozadí), aniž by pro ně musela doručovat zprávy s řazením.</span><span class="sxs-lookup"><span data-stu-id="977f9-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="977f9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="977f9-115">Requirements</span></span>  
 <span data-ttu-id="977f9-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="977f9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="977f9-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="977f9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="977f9-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="977f9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="977f9-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="977f9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="977f9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="977f9-120">See also</span></span>

- [<span data-ttu-id="977f9-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="977f9-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="977f9-122">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="977f9-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)
