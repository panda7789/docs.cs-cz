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
ms.openlocfilehash: 8b02f70f22a7d35bf0fe7816a52c490f88b31217
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218430"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="238f6-102">ICorProfilerThreadEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="238f6-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="238f6-103">Získá počet vláken, která jsou v aplikaci použít.</span><span class="sxs-lookup"><span data-stu-id="238f6-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="238f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="238f6-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="238f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="238f6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="238f6-106">[out] Počet vláken v aplikaci použít.</span><span class="sxs-lookup"><span data-stu-id="238f6-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="238f6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="238f6-107">Requirements</span></span>  
 <span data-ttu-id="238f6-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="238f6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="238f6-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="238f6-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="238f6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="238f6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="238f6-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="238f6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238f6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="238f6-112">See also</span></span>

- [<span data-ttu-id="238f6-113">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="238f6-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="238f6-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="238f6-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
