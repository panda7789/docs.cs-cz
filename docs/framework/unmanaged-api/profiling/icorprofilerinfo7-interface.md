---
title: "ICorProfilerInfo7 rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85bf82a01f431e42a5714eeb54e17a34314534
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="39552-102">ICorProfilerInfo7 rozhraní</span><span class="sxs-lookup"><span data-stu-id="39552-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="39552-103">[V podporované [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="39552-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="39552-104">Podtřídou třídy [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) poskytuje metodu použít nově definovaná metadata modulu, který poskytuje přístup k datovému proudu symbol v paměti.</span><span class="sxs-lookup"><span data-stu-id="39552-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39552-105">Metody</span><span class="sxs-lookup"><span data-stu-id="39552-105">Methods</span></span>  
  
|<span data-ttu-id="39552-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="39552-106">Method</span></span>|<span data-ttu-id="39552-107">Popis</span><span class="sxs-lookup"><span data-stu-id="39552-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39552-108">ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="39552-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="39552-109">Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="39552-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="39552-110">GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="39552-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="39552-111">Vrátí délku datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="39552-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="39552-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="39552-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="39552-113">Čte bajtů z datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="39552-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39552-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39552-114">Requirements</span></span>  
 <span data-ttu-id="39552-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39552-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39552-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="39552-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39552-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39552-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39552-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="39552-118">See Also</span></span>  
 [<span data-ttu-id="39552-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="39552-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
