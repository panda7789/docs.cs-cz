---
title: ICorProfilerThreadEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b803c83b905df47b3957e07c0d64e7ce6f6d303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455475"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="01313-102">ICorProfilerThreadEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="01313-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="01313-103">Získá počet vláken, které používají aplikace.</span><span class="sxs-lookup"><span data-stu-id="01313-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01313-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01313-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01313-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01313-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="01313-106">[out] Počet vláken používaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="01313-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01313-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01313-107">Requirements</span></span>  
 <span data-ttu-id="01313-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01313-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01313-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01313-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01313-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01313-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01313-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01313-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01313-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="01313-112">See Also</span></span>  
 [<span data-ttu-id="01313-113">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01313-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="01313-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="01313-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
