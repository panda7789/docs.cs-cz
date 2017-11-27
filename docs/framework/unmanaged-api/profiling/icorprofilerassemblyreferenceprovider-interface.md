---
title: "Rozhraní ICorProfilerAssemblyReferenceProvider"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerAssemblyReferenceProvider
api_location: mscorwks.dll
api_type: COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2120e400d4ecd23c86cdae7b12d8706b35e8ca08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="b282f-102">Rozhraní ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="b282f-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="b282f-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="b282f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b282f-104">Umožňuje profileru k informování modul CLR (CLR) odkazů na sestavení, které profileru přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b282f-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b282f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b282f-105">Methods</span></span>  
  
|<span data-ttu-id="b282f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b282f-106">Method</span></span>|<span data-ttu-id="b282f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b282f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b282f-108">Metoda AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="b282f-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="b282f-109">Informuje o modulu CLR odkaz na sestavení, který profileru přidat [moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b282f-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b282f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b282f-110">Remarks</span></span>  
 <span data-ttu-id="b282f-111">Modul CLR předá profileru `ICorProfilerAssemblyReferenceProvider` objekt rozhraní v [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b282f-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="b282f-112">To umožňuje profileru k informování CLR odkazů na sestavení, které profileru plánuje přidat později v [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="b282f-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="b282f-113">zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="b282f-113">callback.</span></span> <span data-ttu-id="b282f-114">Tím se zlepšuje přesnost walkera uzavření referenční sestavení modulu CLR a jeho algoritmy pro určení, zda může sdílet sestavení.</span><span class="sxs-lookup"><span data-stu-id="b282f-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="b282f-115">Toto rozhraní je možné pouze v [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání, které se předá tento objekt rozhraní profileru.</span><span class="sxs-lookup"><span data-stu-id="b282f-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b282f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b282f-116">Requirements</span></span>  
 <span data-ttu-id="b282f-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b282f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b282f-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b282f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b282f-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b282f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b282f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b282f-120">See Also</span></span>  
 [<span data-ttu-id="b282f-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b282f-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
