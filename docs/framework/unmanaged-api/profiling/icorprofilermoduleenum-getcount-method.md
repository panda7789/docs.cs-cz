---
title: "ICorProfilerModuleEnum::GetCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62cc7122e25d43998053f0f102e1079252d4d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="228b9-102">ICorProfilerModuleEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="228b9-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="228b9-103">Získá počet spravované moduly, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="228b9-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="228b9-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="228b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="228b9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="228b9-106">[out] Počet modulů runtime v kolekci.</span><span class="sxs-lookup"><span data-stu-id="228b9-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228b9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="228b9-107">Requirements</span></span>  
 <span data-ttu-id="228b9-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="228b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="228b9-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="228b9-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="228b9-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="228b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="228b9-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="228b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228b9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="228b9-112">See Also</span></span>  
 [<span data-ttu-id="228b9-113">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="228b9-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="228b9-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="228b9-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
