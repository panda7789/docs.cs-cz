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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5061750489c74e0385f2ce020c88518604b3167
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169283"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="5699b-102">ICorProfilerFunctionEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="5699b-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="5699b-103">Získá počet funkcí, které byly načteny aplikací nebo vynuceně načíst pomocí profileru.</span><span class="sxs-lookup"><span data-stu-id="5699b-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5699b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5699b-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5699b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5699b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5699b-106">[out] Počet funkcí, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="5699b-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5699b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5699b-107">Requirements</span></span>  
 <span data-ttu-id="5699b-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5699b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5699b-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5699b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5699b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5699b-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5699b-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5699b-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5699b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5699b-112">See also</span></span>

- [<span data-ttu-id="5699b-113">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5699b-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="5699b-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5699b-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
