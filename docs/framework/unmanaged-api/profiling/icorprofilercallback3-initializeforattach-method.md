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
ms.openlocfilehash: 9bff594d0307153fb468b28c1535977f06997748
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499711"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="5d781-102">ICorProfilerCallback3::InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="5d781-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="5d781-103">Volá se modulem CLR (Common Language Runtime), aby Profiler mohl po operaci připojení inicializovat svůj stav.</span><span class="sxs-lookup"><span data-stu-id="5d781-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d781-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d781-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d781-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d781-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="5d781-106">pro Ukazatel rozhraní pro `ICorProfilerInfo*` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5d781-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="5d781-107">pro Ukazatel na data předaná metodě [IClrProfiling:: AttachProfiler –](iclrprofiling-attachprofiler-method.md) v `pvClientData` parametru.</span><span class="sxs-lookup"><span data-stu-id="5d781-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="5d781-108">Pokud má tento parametr hodnotu null, `cbClientData` bude 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="5d781-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="5d781-109">Modul CLR uvolní tuto paměť, když se vrátí z `InitializeForAttach` .</span><span class="sxs-lookup"><span data-stu-id="5d781-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="5d781-110">pro Velikost dat, která odkazuje na velikost (v bajtech) `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="5d781-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d781-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d781-111">Remarks</span></span>  
 <span data-ttu-id="5d781-112">Rozhraní CLR volá, `InitializeForAttach` aby Profiler mohl podat možnost požádat o zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="5d781-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d781-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d781-113">Requirements</span></span>  
 <span data-ttu-id="5d781-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d781-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d781-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5d781-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d781-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d781-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d781-117">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d781-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d781-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d781-118">See also</span></span>

- [<span data-ttu-id="5d781-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d781-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5d781-120">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d781-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="5d781-121">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5d781-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5d781-122">Profilace</span><span class="sxs-lookup"><span data-stu-id="5d781-122">Profiling</span></span>](index.md)
