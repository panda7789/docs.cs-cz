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
ms.openlocfilehash: 50fe7399896c35c1d6595b2d7214280e3009fab5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455798"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="3425f-102">ICorProfilerCallback3::InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="3425f-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="3425f-103">Voláno rozhraním modul CLR (CLR) umožnit profileru příležitost k chybě při inicializaci stav po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="3425f-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3425f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3425f-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3425f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3425f-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="3425f-106">[v] Ukazatele rozhraní pro `ICorProfilerInfo*` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3425f-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="3425f-107">[v] Předaný ukazatel na data [iclrprofiling::attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda v jeho `pvClientData` parametr.</span><span class="sxs-lookup"><span data-stu-id="3425f-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="3425f-108">Pokud tento parametr hodnotu null, `cbClientData` bude 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="3425f-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="3425f-109">Modul CLR uvolní tuto paměť, až se obnoví z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="3425f-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="3425f-110">[v] Velikost v bajtech dat, která `pvClientData` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="3425f-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3425f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3425f-111">Remarks</span></span>  
 <span data-ttu-id="3425f-112">Volání CLR `InitializeForAttach` umožňuje profileru příležitost k žádosti o zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="3425f-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3425f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3425f-113">Requirements</span></span>  
 <span data-ttu-id="3425f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3425f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3425f-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3425f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3425f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3425f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3425f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3425f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3425f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3425f-118">See Also</span></span>  
 [<span data-ttu-id="3425f-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3425f-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3425f-120">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3425f-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="3425f-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3425f-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3425f-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="3425f-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
