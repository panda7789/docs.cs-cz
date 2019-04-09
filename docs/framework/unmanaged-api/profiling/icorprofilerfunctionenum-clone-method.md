---
title: ICorProfilerFunctionEnum::Clone – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ffd1fcc36f0c6cc3c5f063c5a916e8918839566
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135587"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="9ac7e-102">ICorProfilerFunctionEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="9ac7e-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="9ac7e-103">Získá ukazatel rozhraní na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ac7e-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ac7e-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ac7e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9ac7e-106">[out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ac7e-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="9ac7e-107">Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet.</span><span class="sxs-lookup"><span data-stu-id="9ac7e-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="9ac7e-108">Pozice kurzoru počáteční kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="9ac7e-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac7e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ac7e-109">Requirements</span></span>  
 <span data-ttu-id="9ac7e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac7e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac7e-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ac7e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ac7e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ac7e-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9ac7e-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9ac7e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ac7e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ac7e-114">See also</span></span>

- [<span data-ttu-id="9ac7e-115">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ac7e-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="9ac7e-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9ac7e-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
