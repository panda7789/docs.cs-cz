---
title: ICorProfilerThreadEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0301334621a2e393a59e7cc34f2964450a81213f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074167"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="067c9-102">ICorProfilerThreadEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="067c9-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="067c9-103">Získá ukazatel rozhraní na kopii této [icorprofilerthreadenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="067c9-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="067c9-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="067c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="067c9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="067c9-106">[out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilerthreadenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="067c9-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="067c9-107">Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet.</span><span class="sxs-lookup"><span data-stu-id="067c9-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="067c9-108">Pozice kurzoru počáteční kopie je však stejný jako tato aktuálním umístěním kurzoru čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="067c9-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067c9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="067c9-109">Requirements</span></span>  
 <span data-ttu-id="067c9-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="067c9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="067c9-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="067c9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="067c9-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="067c9-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="067c9-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="067c9-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="067c9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="067c9-114">See also</span></span>

- [<span data-ttu-id="067c9-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="067c9-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="067c9-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="067c9-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
