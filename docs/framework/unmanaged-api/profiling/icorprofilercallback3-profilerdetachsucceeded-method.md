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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52803fc04aa55f40a131e2d53dc4ef7dba70bcde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727115"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="43bf0-102">ICorProfilerCallback3::ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="43bf0-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="43bf0-103">Oznámí profileru, že modul CLR (CLR) se chystá uvolnění knihovny DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="43bf0-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43bf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43bf0-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="43bf0-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="43bf0-105">Return Value</span></span>  
 <span data-ttu-id="43bf0-106">Hodnota vrácená z této zpětné volání se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="43bf0-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43bf0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43bf0-107">Remarks</span></span>  
 <span data-ttu-id="43bf0-108">`ProfilerDetachSucceeded` Zpětného volání je vydána po všechna vlákna odpojili profileru kód.</span><span class="sxs-lookup"><span data-stu-id="43bf0-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="43bf0-109">Když tato metoda je volána, profiler by měl provádět žádné poslední minuty úlohy, které nejsou vhodné pro jeho destruktor, jako je například upozornění jeho uživatelské rozhraní nebo protokolování součásti.</span><span class="sxs-lookup"><span data-stu-id="43bf0-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="43bf0-110">Však nesmí volat funkce rozhraní, které jsou k dispozici v modulu CLR při tomto zpětném volání profileru (například [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo `IMetaData*` rozhraní).</span><span class="sxs-lookup"><span data-stu-id="43bf0-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="43bf0-111">Modul CLR vytvoří záznam v protokolu událostí Windows aplikace označující, jestli se operace odpojení úspěšně dokončila.</span><span class="sxs-lookup"><span data-stu-id="43bf0-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="43bf0-112">Po profiler vrátí z této zpětné volání, CLR uvolní objekt profileru a uvolní profiler DLL.</span><span class="sxs-lookup"><span data-stu-id="43bf0-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="43bf0-113">Proto profiler nesmí provádět všechny akce, které by mohly způsobit provedení dotazu uvnitř knihovny DLL profileru po jeho vrácení z této zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="43bf0-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="43bf0-114">Například se nesmí vytvořit vlákna nebo registrace zpětných volání časovače.</span><span class="sxs-lookup"><span data-stu-id="43bf0-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43bf0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43bf0-115">Requirements</span></span>  
 <span data-ttu-id="43bf0-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43bf0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43bf0-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43bf0-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43bf0-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43bf0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43bf0-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43bf0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43bf0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43bf0-120">See also</span></span>
- [<span data-ttu-id="43bf0-121">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="43bf0-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="43bf0-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43bf0-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="43bf0-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="43bf0-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="43bf0-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="43bf0-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
