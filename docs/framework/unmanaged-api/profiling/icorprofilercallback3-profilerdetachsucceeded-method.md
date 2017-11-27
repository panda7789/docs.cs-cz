---
title: "ICorProfilerCallback3::ProfilerDetachSucceeded – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4413e5c475bce6d6f2eea1f7a968c946237f47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="d9f5e-102">ICorProfilerCallback3::ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="d9f5e-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="d9f5e-103">Upozorní profileru, že modul CLR (CLR) má uvolnit knihovnu DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9f5e-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d9f5e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9f5e-105">Return Value</span></span>  
 <span data-ttu-id="d9f5e-106">Vrácená hodnota z této zpětné volání se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9f5e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9f5e-107">Remarks</span></span>  
 <span data-ttu-id="d9f5e-108">`ProfilerDetachSucceeded` Zpětné volání se objeví po všechna vlákna se odpojili profileru kódu.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="d9f5e-109">Když tato metoda je volána, proveďte profileru poslední minutu úkoly, které nejsou vhodné pro jeho destruktor, jako je například upozornění jeho uživatelského rozhraní nebo součást protokolování.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="d9f5e-110">Ale profileru nesmějí provádět volání funkce na rozhraní, které jsou k dispozici CLR během této zpětného volání (například [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo `IMetaData*` rozhraní).</span><span class="sxs-lookup"><span data-stu-id="d9f5e-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="d9f5e-111">Modul CLR vytvoří záznam v protokolu událostí aplikace systému Windows k označení, že byla úspěšně dokončena operace odpojení.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="d9f5e-112">Po návratu profileru z této zpětného volání modulu CLR uvolní objekt profileru a uvolní profileru knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="d9f5e-113">Proto profileru nesmí provádět všechny akce, které by způsobily provádění nastat uvnitř profileru DLL po vrátí z této zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="d9f5e-114">Například nemůže vytvořit podprocesy ani registrace zpětných volání časovače.</span><span class="sxs-lookup"><span data-stu-id="d9f5e-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9f5e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9f5e-115">Requirements</span></span>  
 <span data-ttu-id="d9f5e-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9f5e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f5e-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9f5e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9f5e-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9f5e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9f5e-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9f5e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f5e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9f5e-120">See Also</span></span>  
 [<span data-ttu-id="d9f5e-121">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="d9f5e-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="d9f5e-122">Icorprofilerinfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9f5e-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="d9f5e-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d9f5e-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d9f5e-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="d9f5e-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
