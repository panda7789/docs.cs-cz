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
ms.openlocfilehash: d0219751987b1f2d78ee37a1553b323014c1ccfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865685"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="3dac5-102">ICorProfilerCallback3::InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="3dac5-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="3dac5-103">Volá se modulem CLR (Common Language Runtime), aby Profiler mohl po operaci připojení inicializovat svůj stav.</span><span class="sxs-lookup"><span data-stu-id="3dac5-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dac5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dac5-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dac5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dac5-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="3dac5-106">pro Ukazatel rozhraní pro rozhraní `ICorProfilerInfo*`.</span><span class="sxs-lookup"><span data-stu-id="3dac5-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="3dac5-107">pro Ukazatel na data předaná metodě [IClrProfiling:: AttachProfiler –](iclrprofiling-attachprofiler-method.md) ve svém parametru `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="3dac5-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="3dac5-108">Pokud má tento parametr hodnotu null, `cbClientData` bude 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="3dac5-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="3dac5-109">Modul CLR uvolní tuto paměť při návratu z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="3dac5-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="3dac5-110">pro Velikost dat, která `pvClientData` odkazuje, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3dac5-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dac5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dac5-111">Remarks</span></span>  
 <span data-ttu-id="3dac5-112">Modul CLR volá `InitializeForAttach`, aby Profiler mohl podat možnost požádat o zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="3dac5-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dac5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dac5-113">Requirements</span></span>  
 <span data-ttu-id="3dac5-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dac5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dac5-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3dac5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3dac5-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3dac5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dac5-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dac5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dac5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dac5-118">See also</span></span>

- [<span data-ttu-id="3dac5-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dac5-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3dac5-120">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dac5-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3dac5-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3dac5-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3dac5-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="3dac5-122">Profiling</span></span>](index.md)
