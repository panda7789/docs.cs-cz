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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d63dd911a5f674a3ce0b02ec78de443c7aebf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747168"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="c6a63-102">ICorProfilerCallback::Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="c6a63-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="c6a63-103">Oznámí profileru, že se aplikace vypíná.</span><span class="sxs-lookup"><span data-stu-id="c6a63-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6a63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6a63-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c6a63-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6a63-105">Remarks</span></span>  
 <span data-ttu-id="c6a63-106">Profiler kódu nelze bezpečně volat metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) rozhraní po `Shutdown` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="c6a63-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="c6a63-107">Všechna volání do `ICorProfilerInfo` metody za následek nedefinované chování po `Shutdown` metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c6a63-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="c6a63-108">Určité neměnné události může stále dojít po vypnutí; profiler byste měli věnovat pozornost k vrácení okamžitě, pokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="c6a63-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="c6a63-109">`Shutdown` Metoda bude volána pouze v případě, že spravovaná aplikace, která je právě profilována spuštěn jako spravovaný kód (to znamená, je spravovaný počáteční rámec v zásobníku proces).</span><span class="sxs-lookup"><span data-stu-id="c6a63-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="c6a63-110">Pokud aplikace spustil jako nespravovaný kód, ale později vstupovat do spravovaného kódu, a tím vytvoření instance modulu common language runtime (CLR), pak `Shutdown` nebude volána.</span><span class="sxs-lookup"><span data-stu-id="c6a63-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="c6a63-111">Pro tyto případy, by měl obsahovat profileru v jeho knihovně `DllMain` rutiny, které používají DLL_PROCESS_DETACH hodnota uvolněte veškeré prostředky a provádět čištění zpracování nad svými daty, jako je vyprazdňování trasování na disk a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c6a63-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="c6a63-112">Obecně platí profiler musí zvládnout neočekávané vypnutí.</span><span class="sxs-lookup"><span data-stu-id="c6a63-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="c6a63-113">Například může být proces zastavení na Win32 `TerminateProcess` – metoda (deklarované v Winbase.h).</span><span class="sxs-lookup"><span data-stu-id="c6a63-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="c6a63-114">V jiných případech zastaví CLR bez doručováním zpráv řádné zničení pro ně určité spravovaná vlákna (vláken na pozadí).</span><span class="sxs-lookup"><span data-stu-id="c6a63-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6a63-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6a63-115">Requirements</span></span>  
 <span data-ttu-id="c6a63-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6a63-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6a63-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6a63-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6a63-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6a63-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6a63-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6a63-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a63-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6a63-120">See also</span></span>

- [<span data-ttu-id="c6a63-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6a63-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c6a63-122">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="c6a63-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
