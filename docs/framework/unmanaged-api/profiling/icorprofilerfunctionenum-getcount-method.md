---
title: ICorProfilerFunctionEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 5ccd90e92e83d7f9f6f19a082fb84dc1f1c35f4c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447815"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="91a0b-102">ICorProfilerFunctionEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="91a0b-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="91a0b-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span><span class="sxs-lookup"><span data-stu-id="91a0b-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91a0b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91a0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91a0b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="91a0b-106">[out] The number of functions that were loaded.</span><span class="sxs-lookup"><span data-stu-id="91a0b-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a0b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91a0b-107">Requirements</span></span>  
 <span data-ttu-id="91a0b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a0b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a0b-109">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91a0b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91a0b-110">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91a0b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91a0b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a0b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a0b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91a0b-112">See also</span></span>

- [<span data-ttu-id="91a0b-113">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91a0b-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="91a0b-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="91a0b-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
