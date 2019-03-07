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
ms.openlocfilehash: 3e30cc8ff320c1a4a9a69fb2a07427ef4c8a4149
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485366"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="60a4f-102">ICorProfilerFunctionEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="60a4f-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="60a4f-103">Získá ukazatel rozhraní na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60a4f-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60a4f-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60a4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60a4f-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="60a4f-106">[out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60a4f-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="60a4f-107">Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet.</span><span class="sxs-lookup"><span data-stu-id="60a4f-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="60a4f-108">Pozice kurzoru počáteční kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="60a4f-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a4f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60a4f-109">Requirements</span></span>  
 <span data-ttu-id="60a4f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a4f-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60a4f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60a4f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60a4f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a4f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a4f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60a4f-114">See also</span></span>
- [<span data-ttu-id="60a4f-115">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60a4f-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="60a4f-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="60a4f-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
