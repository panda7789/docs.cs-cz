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
ms.openlocfilehash: 83e32b2b69d53772f8a4ebaabe1c025b95d1da47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453724"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="c7a3b-102">ICorProfilerCallback::Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="c7a3b-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="c7a3b-103">Aby se aplikace vypíná upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7a3b-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7a3b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7a3b-105">Remarks</span></span>  
 <span data-ttu-id="c7a3b-106">Kód profileru nelze bezpečně volat metody [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) rozhraní po `Shutdown` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="c7a3b-107">Volání `ICorProfilerInfo` metody za následek nedefinované chování po `Shutdown` metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="c7a3b-108">Určité neměnné události může stále dojít po vypnutí; vrátit okamžitě v takovém případě by měl postará profileru.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="c7a3b-109">`Shutdown` Volání metody pouze v případě, že spravované aplikace, která je vytvořený profil spustit jako spravovaného kódu (to znamená, je spravován na počáteční rámce v zásobníku proces).</span><span class="sxs-lookup"><span data-stu-id="c7a3b-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="c7a3b-110">Pokud aplikace spustit jako nespravovaný kód, ale později přešli do spravovaného kódu, čímž vytvoření instance common language runtime (CLR), pak `Shutdown` nebude volána.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="c7a3b-111">Pro tyto případy by měla obsahovat profileru své knihovny `DllMain` rutiny, která používá DLL_PROCESS_DETACH hodnotu uvolněte všechny prostředky a provést čištění zpracování svá data, jako je například, abyste vyprázdnili trasování na disk a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="c7a3b-112">Obecně platí musí profileru zvládl neočekávané vypnutí systému.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="c7a3b-113">Například může být proces byl zastaven na Win32 `TerminateProcess` – metoda (deklarované v Winbase.h).</span><span class="sxs-lookup"><span data-stu-id="c7a3b-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="c7a3b-114">V ostatních případech se modulu CLR zastaví určité spravovaných vláknech (vlákna na pozadí) bez doručování zpráv řádné odstraňování pro ně.</span><span class="sxs-lookup"><span data-stu-id="c7a3b-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a3b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7a3b-115">Requirements</span></span>  
 <span data-ttu-id="c7a3b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a3b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a3b-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7a3b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7a3b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7a3b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7a3b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a3b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a3b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7a3b-120">See Also</span></span>  
 [<span data-ttu-id="c7a3b-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7a3b-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c7a3b-122">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="c7a3b-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
