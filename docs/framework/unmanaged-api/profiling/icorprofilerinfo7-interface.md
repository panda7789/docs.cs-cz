---
title: ICorProfilerInfo7 – rozhraní
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495486"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="9d512-102">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d512-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="9d512-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="9d512-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="9d512-104">Podtřída [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , která poskytuje metodu pro použití nově definovaných metadat pro modul a který poskytuje přístup k datovému proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="9d512-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d512-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9d512-105">Methods</span></span>  
  
|<span data-ttu-id="9d512-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d512-106">Method</span></span>|<span data-ttu-id="9d512-107">Description</span><span class="sxs-lookup"><span data-stu-id="9d512-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d512-108">ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="9d512-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="9d512-109">Aplikuje metadata nově definovaná `IMetadataEmit::Define*` metodami na zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="9d512-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="9d512-110">GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="9d512-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="9d512-111">Vrátí délku datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="9d512-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="9d512-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="9d512-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="9d512-113">Načte bajty z datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="9d512-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d512-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d512-114">Requirements</span></span>  
 <span data-ttu-id="9d512-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d512-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d512-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d512-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d512-117">**Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d512-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d512-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d512-118">See also</span></span>

- [<span data-ttu-id="9d512-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9d512-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
