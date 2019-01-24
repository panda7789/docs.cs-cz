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
ms.openlocfilehash: ded15608337d040ab58cb5be45deac4711668ac3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576171"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="c4f0f-102">ICorProfilerFunctionEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="c4f0f-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="c4f0f-103">Získá ukazatel rozhraní na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4f0f-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4f0f-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4f0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4f0f-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c4f0f-106">[out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4f0f-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="c4f0f-107">Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet.</span><span class="sxs-lookup"><span data-stu-id="c4f0f-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="c4f0f-108">Pozice kurzoru počáteční kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="c4f0f-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4f0f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4f0f-109">Requirements</span></span>  
 <span data-ttu-id="c4f0f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4f0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4f0f-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4f0f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4f0f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4f0f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4f0f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4f0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f0f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4f0f-114">See also</span></span>
- [<span data-ttu-id="c4f0f-115">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4f0f-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="c4f0f-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c4f0f-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
