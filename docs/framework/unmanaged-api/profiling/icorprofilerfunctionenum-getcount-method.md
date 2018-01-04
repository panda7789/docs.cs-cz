---
title: "ICorProfilerFunctionEnum::GetCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.GetCount Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ac7e1e4c13578859c02f531dbc3b5e6f01e55cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="78554-102">ICorProfilerFunctionEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="78554-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="78554-103">Získá počet funkcí, které byly v aplikaci nebo vynuceně načteny profileru.</span><span class="sxs-lookup"><span data-stu-id="78554-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78554-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78554-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78554-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78554-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="78554-106">[out] Počet funkcí, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="78554-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78554-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78554-107">Requirements</span></span>  
 <span data-ttu-id="78554-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78554-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78554-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78554-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78554-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78554-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78554-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78554-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78554-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="78554-112">See Also</span></span>  
 [<span data-ttu-id="78554-113">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78554-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="78554-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="78554-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
