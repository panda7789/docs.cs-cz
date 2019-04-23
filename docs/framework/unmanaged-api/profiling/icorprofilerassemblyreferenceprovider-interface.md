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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bad1cc71b9a27896141837a6d342f2cfe068fc5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089728"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="9e700-102">Rozhraní ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="9e700-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="9e700-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="9e700-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9e700-104">Umožňuje profileru informovat common language runtime (CLR) z odkazů na sestavení, které profiler přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9e700-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e700-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9e700-105">Methods</span></span>  
  
|<span data-ttu-id="9e700-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e700-106">Method</span></span>|<span data-ttu-id="9e700-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9e700-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e700-108">AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="9e700-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="9e700-109">Informuje o tom CLR, který profiler má v plánu přidat odkaz na sestavení [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9e700-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e700-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e700-110">Remarks</span></span>  
 <span data-ttu-id="9e700-111">Předá profiler CLR `ICorProfilerAssemblyReferenceProvider` objektu rozhraní v [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9e700-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="9e700-112">To umožňuje profileru CLR odkazy na sestavení, které profiler má v plánu přidat později v informovat [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="9e700-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="9e700-113">zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="9e700-113">callback.</span></span> <span data-ttu-id="9e700-114">Tím se zlepšuje přesnost walker uzavření odkaz na sestavení modulu CLR a její algoritmy pro určení, zda může být sdílené sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e700-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="9e700-115">Toto rozhraní lze použít pouze ve [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání, které se předá tento objekt rozhraní profileru.</span><span class="sxs-lookup"><span data-stu-id="9e700-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e700-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e700-116">Requirements</span></span>  
 <span data-ttu-id="9e700-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e700-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e700-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e700-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e700-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e700-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e700-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e700-120">See also</span></span>

- [<span data-ttu-id="9e700-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9e700-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
