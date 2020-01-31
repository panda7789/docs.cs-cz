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
ms.openlocfilehash: 490f9dd5446a51bd07881cdb9825d737e380a63e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865854"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="fbb78-102">ICorProfilerCallback::Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb78-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="fbb78-103">Oznamuje profileru, že se aplikace vypíná.</span><span class="sxs-lookup"><span data-stu-id="fbb78-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbb78-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fbb78-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbb78-105">Remarks</span></span>  
 <span data-ttu-id="fbb78-106">Kód profileru nemůže bezpečně volat metody rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) po volání metody `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="fbb78-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="fbb78-107">Jakákoli volání metod `ICorProfilerInfo` způsobí nedefinované chování po návratu metody `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="fbb78-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="fbb78-108">K určitým neměnným událostem může docházet i po vypnutí. Profiler by měl být při výskytu okamžitě vrácen.</span><span class="sxs-lookup"><span data-stu-id="fbb78-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="fbb78-109">Metoda `Shutdown` bude volána pouze v případě, že je spravovaná aplikace, která je profilovaná, spuštěná jako spravovaný kód (tj. počáteční rámec na zásobníku procesu je spravovaný).</span><span class="sxs-lookup"><span data-stu-id="fbb78-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="fbb78-110">Pokud se aplikace spustila jako nespravovaný kód, ale později se přeskočí do spravovaného kódu, vytvoří se instance modulu CLR (Common Language Runtime), a poté `Shutdown` nebude volána.</span><span class="sxs-lookup"><span data-stu-id="fbb78-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="fbb78-111">V těchto případech by měl Profiler ve své knihovně zahrnovat `DllMain` rutinu, která používá hodnotu DLL_PROCESS_DETACH k uvolnění prostředků a k vyčištění zpracování dat, jako je například vyprazdňování trasování na disk a tak dále.</span><span class="sxs-lookup"><span data-stu-id="fbb78-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="fbb78-112">Obecně platí, že Profiler se musí vypořádat s neočekávanými vypnutími.</span><span class="sxs-lookup"><span data-stu-id="fbb78-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="fbb78-113">Například proces může být zastaven metodou Win32's `TerminateProcess` (deklarovaným v Winbase. h).</span><span class="sxs-lookup"><span data-stu-id="fbb78-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="fbb78-114">V ostatních případech CLR zachová určitá spravovaná vlákna (vlákna na pozadí), aniž by pro ně musela doručovat zprávy s řazením.</span><span class="sxs-lookup"><span data-stu-id="fbb78-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb78-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbb78-115">Requirements</span></span>  
 <span data-ttu-id="fbb78-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb78-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb78-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fbb78-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbb78-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fbb78-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb78-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb78-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb78-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbb78-120">See also</span></span>

- [<span data-ttu-id="fbb78-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb78-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fbb78-122">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb78-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)
