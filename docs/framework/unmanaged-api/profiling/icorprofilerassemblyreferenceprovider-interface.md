---
title: Rozhraní ICorProfilerAssemblyReferenceProvider
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 17fb3de830d1aed2214631bbe8254a7f58030025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500517"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="c1f97-102">Rozhraní ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="c1f97-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="c1f97-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="c1f97-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c1f97-104">Umožňuje profileru informovat modul CLR (Common Language Runtime) se odkazy na sestavení, které Profiler přidá do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c1f97-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1f97-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c1f97-105">Methods</span></span>  
  
|<span data-ttu-id="c1f97-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c1f97-106">Method</span></span>|<span data-ttu-id="c1f97-107">Description</span><span class="sxs-lookup"><span data-stu-id="c1f97-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1f97-108">Metoda AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="c1f97-108">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="c1f97-109">Informuje modul CLR odkazu na sestavení, který Profiler plánuje přidat do zpětného volání [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c1f97-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f97-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1f97-110">Remarks</span></span>  
 <span data-ttu-id="c1f97-111">Modul CLR předá profileru `ICorProfilerAssemblyReferenceProvider` objekt rozhraní ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c1f97-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="c1f97-112">To umožňuje profileru informovat modul CLR o odkazech na sestavení, které plány profileru později přidají do [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="c1f97-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="c1f97-113">onCuePoint.</span><span class="sxs-lookup"><span data-stu-id="c1f97-113">callback.</span></span> <span data-ttu-id="c1f97-114">Tím se zlepší přesnost prohlížeč ukončení odkazu sestavení CLR a jeho algoritmy pro určení, zda lze sdílet sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1f97-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="c1f97-115">Toto rozhraní lze použít pouze ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) , které předá tento objekt rozhraní profileru.</span><span class="sxs-lookup"><span data-stu-id="c1f97-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f97-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1f97-116">Requirements</span></span>  
 <span data-ttu-id="c1f97-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1f97-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f97-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c1f97-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1f97-119">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f97-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f97-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1f97-120">See also</span></span>

- [<span data-ttu-id="c1f97-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c1f97-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
