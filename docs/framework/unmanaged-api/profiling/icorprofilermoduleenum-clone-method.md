---
title: "ICorProfilerModuleEnum::Clone – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d6e5da0912c1926fea4afe513e7140055052416
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="73a2a-102">ICorProfilerModuleEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="73a2a-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="73a2a-103">Získá ukazatele rozhraní v kopii [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73a2a-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73a2a-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73a2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73a2a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="73a2a-106">[out] Ukazatel na ukazatel rozhraní, která naopak odkazuje na kopii této [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73a2a-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="73a2a-107">Kopii enumerátor udržuje vlastní stav výčtu odděleně od této enumerátor.</span><span class="sxs-lookup"><span data-stu-id="73a2a-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="73a2a-108">Pozice kurzoru počáteční vytvoření kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="73a2a-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73a2a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73a2a-109">Requirements</span></span>  
 <span data-ttu-id="73a2a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73a2a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a2a-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73a2a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73a2a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73a2a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73a2a-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73a2a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a2a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="73a2a-114">See Also</span></span>  
 [<span data-ttu-id="73a2a-115">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73a2a-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="73a2a-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="73a2a-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
