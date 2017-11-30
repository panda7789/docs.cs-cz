---
title: "ICorProfilerCallback3::InitializeForAttach – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.InitializeForAttach Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 323f163774407ff2ddfd261ff6d6584a07ed7d8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="bd87d-102">ICorProfilerCallback3::InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="bd87d-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="bd87d-103">Voláno rozhraním modul CLR (CLR) umožnit profileru příležitost k chybě při inicializaci stav po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="bd87d-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd87d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd87d-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd87d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd87d-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="bd87d-106">[v] Ukazatele rozhraní pro `ICorProfilerInfo*` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd87d-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="bd87d-107">[v] Předaný ukazatel na data [iclrprofiling::attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda v jeho `pvClientData` parametr.</span><span class="sxs-lookup"><span data-stu-id="bd87d-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="bd87d-108">Pokud tento parametr hodnotu null, `cbClientData` bude 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="bd87d-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="bd87d-109">Modul CLR uvolní tuto paměť, až se obnoví z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="bd87d-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="bd87d-110">[v] Velikost v bajtech dat, která `pvClientData` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="bd87d-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd87d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd87d-111">Remarks</span></span>  
 <span data-ttu-id="bd87d-112">Volání CLR `InitializeForAttach` umožňuje profileru příležitost k žádosti o zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="bd87d-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd87d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd87d-113">Requirements</span></span>  
 <span data-ttu-id="bd87d-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd87d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd87d-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd87d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd87d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd87d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd87d-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd87d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd87d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd87d-118">See Also</span></span>  
 [<span data-ttu-id="bd87d-119">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd87d-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="bd87d-120">Icorprofilerinfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd87d-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="bd87d-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="bd87d-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bd87d-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="bd87d-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
