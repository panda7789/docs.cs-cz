---
title: ICorProfilerInfo7 Interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a734bfdef89d4f8f9459f49a3ce2cee83faef9f6
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66250989"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="74aec-102">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74aec-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="74aec-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="74aec-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="74aec-104">Podtřída [icorprofilerinfo6 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) , který poskytuje způsob, jak použít nově definované v modulu metadat, který poskytuje přístup k datovému proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="74aec-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74aec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="74aec-105">Methods</span></span>  
  
|<span data-ttu-id="74aec-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="74aec-106">Method</span></span>|<span data-ttu-id="74aec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="74aec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74aec-108">ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="74aec-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="74aec-109">Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="74aec-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="74aec-110">GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="74aec-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="74aec-111">Vrátí délku datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="74aec-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="74aec-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="74aec-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="74aec-113">Přečte bajtů ze symbolů v paměti datového proudu.</span><span class="sxs-lookup"><span data-stu-id="74aec-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74aec-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74aec-114">Requirements</span></span>  
 <span data-ttu-id="74aec-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74aec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74aec-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74aec-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74aec-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74aec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74aec-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74aec-118">See also</span></span>

- [<span data-ttu-id="74aec-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="74aec-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
