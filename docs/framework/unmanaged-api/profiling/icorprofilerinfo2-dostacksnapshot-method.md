---
title: "ICorProfilerInfo2::DoStackSnapshot – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5548254eb160547643a874fd2e31a085ec6f3ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="73786-102">ICorProfilerInfo2::DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="73786-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>
<span data-ttu-id="73786-103">Provede spravované rámce v zásobníku pro zadaný vlákno a odesílá informace do profileru prostřednictvím zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="73786-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73786-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73786-104">Syntax</span></span>  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73786-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73786-105">Parameters</span></span>  
 `thread`  
 <span data-ttu-id="73786-106">[v] ID cílového vlákno.</span><span class="sxs-lookup"><span data-stu-id="73786-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="73786-107">Předání hodnotou null v `thread` vypočítá snímek aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="73786-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="73786-108">Pokud `ThreadID` z jiné vlákno je předán, modul CLR (CLR) pozastaví daném vláknu, provede snímku a obnoví.</span><span class="sxs-lookup"><span data-stu-id="73786-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="73786-109">[v] Ukazatel na implementaci [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) metodu, která je volána metodou CLR profileru poskytnout informace o každé spravované rámečkem a každé spuštění nespravované rámce.</span><span class="sxs-lookup"><span data-stu-id="73786-109">[in] A pointer to the implementation of the [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="73786-110">`StackSnapshotCallback` Je implementována metoda modul pro zápis profileru.</span><span class="sxs-lookup"><span data-stu-id="73786-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="73786-111">[v] Hodnota [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) výčtu, který určuje množství dat, které mají být předány zpět pro každý snímek pomocí `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="73786-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="73786-112">[v] Ukazatel na klienta data, která je předána přímo do `StackSnapshotCallback` funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="73786-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="73786-113">[v] Ukazatel na Win32 `CONTEXT` strukturu, která se používá k procházení zásobníku počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="73786-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="73786-114">Win32 `CONTEXT` struktura obsahuje hodnoty registrů procesoru a představuje stav procesoru v určitém okamžiku v čase.</span><span class="sxs-lookup"><span data-stu-id="73786-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="73786-115">Počáteční hodnoty pomáhá určit, kde začít procházení zásobníku, pokud je horní části zásobníku kód pomocného objektu nespravované; modulu CLR počáteční hodnoty, jinak hodnota se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="73786-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="73786-116">Je nutné zadat počáteční hodnoty pro asynchronní procházení.</span><span class="sxs-lookup"><span data-stu-id="73786-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="73786-117">Pokud byste synchronní procházení, je nutné žádné počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="73786-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="73786-118">`context` Parametr je platný pouze v případě, že byla předána příznak COR_PRF_SNAPSHOT_CONTEXT `infoFlags` parametr.</span><span class="sxs-lookup"><span data-stu-id="73786-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="73786-119">[v] Velikost `CONTEXT` strukturu, která odkazuje `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="73786-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73786-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73786-120">Remarks</span></span>  
 <span data-ttu-id="73786-121">Předání hodnotou null pro `thread` vypočítá snímek aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="73786-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="73786-122">Snímky lze pořizovat další podprocesy pouze v případě, že cíl vlákno je pozastaveno v době.</span><span class="sxs-lookup"><span data-stu-id="73786-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="73786-123">Profileru chce provede zásobníku, volá `DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="73786-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="73786-124">Před modulu CLR vrátí z tohoto volání, zavolá váš `StackSnapshotCallback` několikrát, jednou pro každý spravovaný rámce (nebo spuštění nespravované rámce) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73786-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="73786-125">Pokud nedojde k nespravované rámce, můžete musí provede je sami.</span><span class="sxs-lookup"><span data-stu-id="73786-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="73786-126">Pořadí, ve kterém je proveden vaši firmu zásobníku je opakem jak snímky byly vloženy do zásobníku: poslední list (poslední nabídnutých) snímek první, hlavní (první nabídnutých) snímku.</span><span class="sxs-lookup"><span data-stu-id="73786-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="73786-127">Další informace o tom, jak program profileru vás spravované zásobníky najdete v tématu [profileru zásobníku proti v rozhraní .NET Framework 2.0: základy a kromě](http://go.microsoft.com/fwlink/?LinkId=73638).</span><span class="sxs-lookup"><span data-stu-id="73786-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](http://go.microsoft.com/fwlink/?LinkId=73638).</span></span>  
  
 <span data-ttu-id="73786-128">Procházení zásobníku může být synchronní nebo asynchronní, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="73786-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="73786-129">Procházení synchronní zásobníku</span><span class="sxs-lookup"><span data-stu-id="73786-129">Synchronous Stack Walk</span></span>  
 <span data-ttu-id="73786-130">Procházení zásobníku synchronní zahrnuje proti zásobník aktuálního vlákna v reakci na zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="73786-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="73786-131">Nevyžaduje se synchronizace replik indexů nebo přechodem do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="73786-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="73786-132">Provedete synchronní, při volání v reakci na CLR volání jedné z vaší profileru [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (nebo [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) volání metody, `DoStackSnapshot` vás zásobník aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="73786-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (or [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="73786-133">To je užitečné, když chcete zobrazit, co se zásobníkem vypadá na oznámení, jako [icorprofilercallback::objectallocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="73786-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="73786-134">Stačí zavolat `DoStackSnapshot` uvnitř vaší `ICorProfilerCallback` metodu a předá hodnotu null v `context` a `thread` parametry.</span><span class="sxs-lookup"><span data-stu-id="73786-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="73786-135">Procházení asynchronní zásobníku</span><span class="sxs-lookup"><span data-stu-id="73786-135">Asynchronous Stack Walk</span></span>  
 <span data-ttu-id="73786-136">Procházení zásobníku asynchronní zahrnuje procházení zásobníku jiné vlákno nebo procházení zásobníku aktuální vlákno, není v odpovědi na zpětné volání, ale podle weby ukazatel instrukce aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="73786-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="73786-137">Asynchronní procházení vyžaduje počáteční hodnoty, pokud je horní části zásobníku nespravovaného kódu, který není součástí platformy vyvolání (kódu PInvoke) nebo volání COM, ale kód pomocného objektu CLR sám sebe.</span><span class="sxs-lookup"><span data-stu-id="73786-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="73786-138">Kód, který nemá kolekci kompilování nebo paměti za běhu (JIT) je například kód pomocného objektu.</span><span class="sxs-lookup"><span data-stu-id="73786-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="73786-139">Získáte počáteční hodnoty tak, že přímo pozastavení vláken cíl a proti jeho zásobníku sami, vyhledejte nejhornější spravovat rámce.</span><span class="sxs-lookup"><span data-stu-id="73786-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="73786-140">Po cíl vlákno je pozastaveno, získáte aktuální kontext registrace vlákno cíl.</span><span class="sxs-lookup"><span data-stu-id="73786-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="73786-141">Dále určit, zda kontext registrace odkazuje na nespravovaný kód voláním [icorprofilerinfo::getfunctionfromip –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) – vrátí-li `FunctionID` rovná nule, je rámečku nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="73786-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="73786-142">Nyní provede v zásobníku, dokud nepřejdete na první spravované rámce, pak vypočítat kontext počáteční hodnoty na základě kontextu registrace pro tento snímek.</span><span class="sxs-lookup"><span data-stu-id="73786-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="73786-143">Volání `DoStackSnapshot` s váš kontext počáteční hodnoty zahájíte procházení asynchronní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73786-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="73786-144">Pokud nezadáte počáteční hodnoty, `DoStackSnapshot` může přeskočit spravované rámce v horní části zásobníku a proto vám poskytne procházení zásobníku neúplné.</span><span class="sxs-lookup"><span data-stu-id="73786-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="73786-145">Pokud zadáte počáteční hodnoty, musí odkazovat na kompilována nebo Native Image Generator (Ngen.exe)-generovaného kódu; v opačném `DoStackSnapshot` vrátí kód chyby CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span><span class="sxs-lookup"><span data-stu-id="73786-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="73786-146">Asynchronní procházení zásobníku můžete snadno způsobit zablokování nebo přistupovat k narušení, pokud jste postupovali podle těchto pokynů:</span><span class="sxs-lookup"><span data-stu-id="73786-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="73786-147">Po pozastavení přímo vláken, mějte na paměti, že pouze vlákno, které má nebude nikdy spuštěn spravovaného kódu můžete pozastavit jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="73786-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
-   <span data-ttu-id="73786-148">Vždy blok ve vaší [icorprofilercallback::threaddestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) zpětného volání až do dokončení daném vláknu procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73786-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
-   <span data-ttu-id="73786-149">Podržte zámek není, pokud vaše profileru zavolá funkci CLR, které můžete aktivovat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="73786-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="73786-150">To znamená není držitelem zámek Pokud vlastnícím vlákno může provádět volání, která aktivuje uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="73786-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="73786-151">K dispozici je také riziko vzájemného zablokování při volání `DoStackSnapshot` z vlákno, které vaše profileru vytvořil, aby můžete projde zásobník samostatný cílový vlákna.</span><span class="sxs-lookup"><span data-stu-id="73786-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="73786-152">První vlákno, které jste vytvořili vstupuje do určité `ICorProfilerInfo*` metody (včetně `DoStackSnapshot`), modul CLR provede inicializaci specifické pro CLR v daném vláknu podle vláken.</span><span class="sxs-lookup"><span data-stu-id="73786-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="73786-153">Pokud vaše profileru pozastavilo vlákno cíl jejichž zásobníku se pokoušíte provede, a pokud daném vláknu cíl se stalo s vlastní zámek potřebné k provedení této inicializace vlákno, dojde k zablokování.</span><span class="sxs-lookup"><span data-stu-id="73786-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="73786-154">Abyste předešli této zablokování, provést počáteční volání do `DoStackSnapshot` z vaší profileru vytvořit vlákno vás samostatné cíle přístup z více vláken, ale není pozastavit nejprve vlákno cíl.</span><span class="sxs-lookup"><span data-stu-id="73786-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="73786-155">Tento počáteční volání zajišťuje, zda inicializace vlákno dokončí bez vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="73786-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="73786-156">Pokud `DoStackSnapshot` úspěšné a alespoň jeden snímek sestavy po tomto okamžiku je bezpečné pro přístup z tohoto profileru vytvořit vlákno pozastavit všechny cílové přístup z více vláken a volání `DoStackSnapshot` projde zásobník daném vláknu cíl.</span><span class="sxs-lookup"><span data-stu-id="73786-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73786-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73786-157">Requirements</span></span>  
 <span data-ttu-id="73786-158">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73786-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73786-159">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73786-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73786-160">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73786-160">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73786-161">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73786-161">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73786-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="73786-162">See Also</span></span>  
 [<span data-ttu-id="73786-163">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73786-163">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="73786-164">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73786-164">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
