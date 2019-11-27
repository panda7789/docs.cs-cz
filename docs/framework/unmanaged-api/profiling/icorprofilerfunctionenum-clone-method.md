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
ms.openlocfilehash: a212a0499b1091f1c77b52951ecef2cb2cace4df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447844"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="9d854-102">ICorProfilerFunctionEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="9d854-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="9d854-103">Získá ukazatel rozhraní na kopii tohoto rozhraní [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9d854-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d854-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d854-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d854-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d854-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9d854-106">mimo Ukazatel na ukazatel rozhraní, který zase odkazuje na kopii tohoto rozhraní [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9d854-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="9d854-107">Kopie enumerátoru udržuje svůj vlastní stav výčtu odděleně od tohoto enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="9d854-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="9d854-108">Počáteční pozice kurzoru pro kopii je však stejná jako aktuální pozice kurzoru tohoto čítače.</span><span class="sxs-lookup"><span data-stu-id="9d854-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d854-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d854-109">Requirements</span></span>  
 <span data-ttu-id="9d854-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d854-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d854-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d854-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d854-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d854-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d854-113">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d854-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d854-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d854-114">See also</span></span>

- [<span data-ttu-id="9d854-115">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d854-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="9d854-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9d854-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
