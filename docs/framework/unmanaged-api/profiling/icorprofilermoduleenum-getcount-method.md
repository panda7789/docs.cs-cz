---
title: ICorProfilerModuleEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 190d6477e0474a7f865f231dbf116e845a403a34
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471183"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="cc931-102">ICorProfilerModuleEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="cc931-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="cc931-103">Získá počet spravované moduly, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc931-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc931-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc931-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc931-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc931-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="cc931-106">[out] Počet modulů runtime v kolekci.</span><span class="sxs-lookup"><span data-stu-id="cc931-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc931-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc931-107">Requirements</span></span>  
 <span data-ttu-id="cc931-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc931-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc931-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc931-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc931-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc931-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc931-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc931-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc931-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc931-112">See also</span></span>
- [<span data-ttu-id="cc931-113">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc931-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="cc931-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="cc931-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
