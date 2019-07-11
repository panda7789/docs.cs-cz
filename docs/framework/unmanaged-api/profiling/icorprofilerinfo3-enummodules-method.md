---
title: ICorProfilerInfo3::EnumModules – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ea379befab7711d1c6bc2d6005cb62d853acce9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756976"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="31d5b-102">ICorProfilerInfo3::EnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="31d5b-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="31d5b-103">Vrátí enumerátor, který poskytuje metody, které postupně iterovat přes kolekci spravované moduly, které se načtou do aplikace.</span><span class="sxs-lookup"><span data-stu-id="31d5b-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31d5b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31d5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31d5b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="31d5b-106">[out] Ukazatel [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31d5b-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d5b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31d5b-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d5b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31d5b-108">Requirements</span></span>  
 <span data-ttu-id="31d5b-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d5b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d5b-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31d5b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31d5b-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31d5b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31d5b-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d5b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d5b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31d5b-113">See also</span></span>

- [<span data-ttu-id="31d5b-114">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31d5b-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="31d5b-115">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31d5b-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="31d5b-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="31d5b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="31d5b-117">Profilace</span><span class="sxs-lookup"><span data-stu-id="31d5b-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
