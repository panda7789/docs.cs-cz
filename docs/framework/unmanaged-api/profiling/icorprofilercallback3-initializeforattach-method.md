---
title: ICorProfilerCallback3::InitializeForAttach – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84d07fe975bab1b0af81299893b52142630b5bb9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079744"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="d7bc3-102">ICorProfilerCallback3::InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="d7bc3-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="d7bc3-103">Volána modulem common language runtime (CLR), která poskytující nástroji pro profilování příležitost k inicializaci svého stavu po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="d7bc3-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7bc3-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7bc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7bc3-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="d7bc3-106">[in] Pro ukazatel rozhraní `ICorProfilerInfo*` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d7bc3-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="d7bc3-107">[in] Předat ukazatel na data [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metodu v jeho `pvClientData` parametru.</span><span class="sxs-lookup"><span data-stu-id="d7bc3-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="d7bc3-108">Pokud má parametr hodnotu null, `cbClientData` 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="d7bc3-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="d7bc3-109">Modul CLR uvolnění tuto paměť návratu z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="d7bc3-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="d7bc3-110">[in] Velikost v bajtech, dat, která `pvClientData` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="d7bc3-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7bc3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7bc3-111">Remarks</span></span>  
 <span data-ttu-id="d7bc3-112">Volání CLR `InitializeForAttach` k poskytující nástroji pro profilování příležitost k žádosti o zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="d7bc3-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7bc3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7bc3-113">Requirements</span></span>  
 <span data-ttu-id="d7bc3-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7bc3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7bc3-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7bc3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7bc3-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7bc3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7bc3-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7bc3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bc3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7bc3-118">See also</span></span>

- [<span data-ttu-id="d7bc3-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7bc3-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d7bc3-120">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7bc3-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d7bc3-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d7bc3-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d7bc3-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="d7bc3-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
