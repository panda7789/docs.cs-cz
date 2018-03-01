---
title: "ICorProfilerFunctionEnum::Clone – metoda"
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
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 449292d8bacd6bb965119da81671c739f12dc3a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="aa50b-102">ICorProfilerFunctionEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="aa50b-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="aa50b-103">Získá ukazatele rozhraní v kopii [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa50b-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa50b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa50b-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa50b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa50b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="aa50b-106">[out] Ukazatel na ukazatel rozhraní, které se pak odkazuje na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa50b-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="aa50b-107">Kopii enumerátor udržuje vlastní stav výčtu odděleně od této enumerátor.</span><span class="sxs-lookup"><span data-stu-id="aa50b-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="aa50b-108">Pozice kurzoru počáteční vytvoření kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="aa50b-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa50b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa50b-109">Requirements</span></span>  
 <span data-ttu-id="aa50b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa50b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa50b-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa50b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa50b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa50b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa50b-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa50b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa50b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa50b-114">See Also</span></span>  
 [<span data-ttu-id="aa50b-115">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa50b-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="aa50b-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="aa50b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
