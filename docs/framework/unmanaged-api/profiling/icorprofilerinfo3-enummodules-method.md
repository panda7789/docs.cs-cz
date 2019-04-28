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
ms.openlocfilehash: be5d05c34272b9fa5755b4d0e22fa9094707c5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703553"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="3eede-102">ICorProfilerInfo3::EnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="3eede-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="3eede-103">Vrátí enumerátor, který poskytuje metody, které postupně iterovat přes kolekci spravované moduly, které se načtou do aplikace.</span><span class="sxs-lookup"><span data-stu-id="3eede-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eede-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eede-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eede-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3eede-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3eede-106">[out] Ukazatel [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3eede-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eede-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3eede-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eede-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3eede-108">Requirements</span></span>  
 <span data-ttu-id="3eede-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eede-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eede-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3eede-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3eede-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eede-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eede-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eede-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eede-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3eede-113">See also</span></span>

- [<span data-ttu-id="3eede-114">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3eede-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="3eede-115">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3eede-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3eede-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3eede-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="3eede-117">Profilace</span><span class="sxs-lookup"><span data-stu-id="3eede-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
