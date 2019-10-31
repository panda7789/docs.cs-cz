---
title: ICorProfilerInfo7 – rozhraní
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125057"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="fa4c8-102">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa4c8-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="fa4c8-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="fa4c8-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="fa4c8-104">Podtřída [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) , která poskytuje metodu pro použití nově definovaných metadat pro modul a který poskytuje přístup k datovému proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="fa4c8-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa4c8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fa4c8-105">Methods</span></span>  
  
|<span data-ttu-id="fa4c8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fa4c8-106">Method</span></span>|<span data-ttu-id="fa4c8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fa4c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa4c8-108">ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="fa4c8-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="fa4c8-109">Aplikuje metadata nově definovaná metodami `IMetadataEmit::Define*` do zadaného modulu.</span><span class="sxs-lookup"><span data-stu-id="fa4c8-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="fa4c8-110">GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="fa4c8-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="fa4c8-111">Vrátí délku datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="fa4c8-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="fa4c8-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="fa4c8-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="fa4c8-113">Načte bajty z datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="fa4c8-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa4c8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa4c8-114">Requirements</span></span>  
 <span data-ttu-id="fa4c8-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa4c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4c8-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fa4c8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa4c8-117">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4c8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa4c8-118">See also</span></span>

- [<span data-ttu-id="fa4c8-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fa4c8-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
