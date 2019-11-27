---
title: ICorProfilerCallback3::ProfilerDetachSucceeded – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: b044c493649b73566a2e70db2e19977a6a7b877d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439456"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="ed6ae-102">ICorProfilerCallback3::ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="ed6ae-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="ed6ae-103">Upozorní profileru, že modul CLR (Common Language Runtime) chystá uvolnění knihovny DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed6ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed6ae-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ed6ae-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed6ae-105">Return Value</span></span>  
 <span data-ttu-id="ed6ae-106">Návratová hodnota z tohoto zpětného volání je ignorována.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed6ae-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed6ae-107">Remarks</span></span>  
 <span data-ttu-id="ed6ae-108">Zpětné volání `ProfilerDetachSucceeded` je vystaveno po ukončení všech vláken v kódu profileru.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="ed6ae-109">Při volání této metody by Profiler měl provést všechny poslední minutové úkoly, které nejsou vhodné pro svůj destruktor, jako je například oznamování jeho uživatelského rozhraní nebo komponenty protokolování.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="ed6ae-110">Profiler však nesmí volat funkce v rozhraních, která jsou poskytována modulem CLR během tohoto zpětného volání (například rozhraní [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo `IMetaData*`).</span><span class="sxs-lookup"><span data-stu-id="ed6ae-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="ed6ae-111">Modul CLR vytvoří položku v protokolu událostí aplikace systému Windows, která indikuje, že operace odpojení je úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="ed6ae-112">Poté, co Profiler vrátí z tohoto zpětného volání, modul CLR uvolní objekt profileru a uvolní knihovnu DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="ed6ae-113">Proto profiler nesmí provádět žádné akce, které by mohly způsobit, že by došlo k provedení v rámci knihovny DLL profileru po návratu z tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="ed6ae-114">Například nesmí vytvářet vlákna nebo registrovat zpětná volání časovače.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed6ae-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed6ae-115">Requirements</span></span>  
 <span data-ttu-id="ed6ae-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed6ae-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed6ae-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed6ae-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed6ae-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed6ae-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed6ae-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed6ae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6ae-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed6ae-120">See also</span></span>

- [<span data-ttu-id="ed6ae-121">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="ed6ae-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ed6ae-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed6ae-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ed6ae-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ed6ae-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ed6ae-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="ed6ae-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
