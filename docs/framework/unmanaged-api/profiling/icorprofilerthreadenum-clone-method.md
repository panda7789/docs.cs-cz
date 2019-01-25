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
ms.openlocfilehash: 5b9d3224370dac0f8a52affef9201e5cbec43de0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547433"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="2a849-102">ICorProfilerThreadEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="2a849-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="2a849-103">Získá ukazatel rozhraní na kopii této [icorprofilerthreadenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a849-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a849-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a849-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a849-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a849-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2a849-106">[out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilerthreadenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a849-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="2a849-107">Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet.</span><span class="sxs-lookup"><span data-stu-id="2a849-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="2a849-108">Pozice kurzoru počáteční kopie je však stejný jako tato aktuálním umístěním kurzoru čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="2a849-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a849-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a849-109">Requirements</span></span>  
 <span data-ttu-id="2a849-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a849-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a849-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a849-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a849-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a849-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a849-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a849-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a849-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a849-114">See also</span></span>
- [<span data-ttu-id="2a849-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="2a849-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="2a849-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2a849-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
