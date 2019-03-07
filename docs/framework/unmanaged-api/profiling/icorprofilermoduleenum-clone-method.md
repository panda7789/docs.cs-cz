---
title: ICorProfilerModuleEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd3e3739ea9b5330f456156c0455009d90478649
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470468"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="27aa1-102">ICorProfilerModuleEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="27aa1-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="27aa1-103">Získá ukazatel rozhraní na kopii této [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27aa1-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27aa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27aa1-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27aa1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27aa1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="27aa1-106">[out] Ukazatel na ukazatel rozhraní, které zase odkazuje na kopii této [icorprofilermoduleenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27aa1-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="27aa1-107">Kopírování čítač udržuje svůj vlastní stav výčtu odděleně od výčet.</span><span class="sxs-lookup"><span data-stu-id="27aa1-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="27aa1-108">Pozice kurzoru počáteční kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="27aa1-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27aa1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27aa1-109">Requirements</span></span>  
 <span data-ttu-id="27aa1-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27aa1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27aa1-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27aa1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27aa1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27aa1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27aa1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27aa1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27aa1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27aa1-114">See also</span></span>
- [<span data-ttu-id="27aa1-115">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27aa1-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="27aa1-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="27aa1-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
