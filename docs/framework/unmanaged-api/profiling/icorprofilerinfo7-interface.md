---
title: ICorProfilerInfo7 Interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786240"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="32629-102">ICorProfilerInfo7 Interface</span><span class="sxs-lookup"><span data-stu-id="32629-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="32629-103">[Podporované v [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="32629-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="32629-104">Podtřída [icorprofilerinfo6 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) , který poskytuje způsob, jak použít nově definované v modulu metadat, který poskytuje přístup k datovému proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="32629-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32629-105">Metody</span><span class="sxs-lookup"><span data-stu-id="32629-105">Methods</span></span>  
  
|<span data-ttu-id="32629-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="32629-106">Method</span></span>|<span data-ttu-id="32629-107">Popis</span><span class="sxs-lookup"><span data-stu-id="32629-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32629-108">ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="32629-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="32629-109">Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="32629-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="32629-110">GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="32629-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="32629-111">Vrátí délku datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="32629-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="32629-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="32629-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="32629-113">Přečte bajtů ze symbolů v paměti datového proudu.</span><span class="sxs-lookup"><span data-stu-id="32629-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32629-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32629-114">Requirements</span></span>  
 <span data-ttu-id="32629-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32629-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32629-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32629-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32629-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32629-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32629-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32629-118">See also</span></span>

- [<span data-ttu-id="32629-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="32629-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
