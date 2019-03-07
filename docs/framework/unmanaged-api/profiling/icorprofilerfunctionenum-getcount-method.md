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
ms.openlocfilehash: 6827a61f670c07595ac78bcd4a8aef201a48b1e0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479131"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="7bb99-102">ICorProfilerFunctionEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7bb99-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="7bb99-103">Získá počet funkcí, které byly načteny aplikací nebo vynuceně načíst pomocí profileru.</span><span class="sxs-lookup"><span data-stu-id="7bb99-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bb99-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bb99-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7bb99-106">[out] Počet funkcí, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="7bb99-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb99-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bb99-107">Requirements</span></span>  
 <span data-ttu-id="7bb99-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb99-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb99-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7bb99-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bb99-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bb99-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bb99-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb99-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb99-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bb99-112">See also</span></span>
- [<span data-ttu-id="7bb99-113">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7bb99-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="7bb99-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7bb99-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
