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
ms.openlocfilehash: 2faa7185202b46e77e501d69bb471391a7c6eb68
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864619"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="99f35-102">ICorProfilerFunctionEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="99f35-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="99f35-103">Získá ukazatel rozhraní na kopii tohoto rozhraní [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="99f35-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99f35-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99f35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99f35-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="99f35-106">mimo Ukazatel na ukazatel rozhraní, který zase odkazuje na kopii tohoto rozhraní [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="99f35-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="99f35-107">Kopie enumerátoru udržuje svůj vlastní stav výčtu odděleně od tohoto enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="99f35-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="99f35-108">Počáteční pozice kurzoru pro kopii je však stejná jako aktuální pozice kurzoru tohoto čítače.</span><span class="sxs-lookup"><span data-stu-id="99f35-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99f35-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99f35-109">Requirements</span></span>  
 <span data-ttu-id="99f35-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99f35-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f35-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="99f35-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99f35-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="99f35-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99f35-113">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99f35-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f35-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99f35-114">See also</span></span>

- [<span data-ttu-id="99f35-115">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99f35-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="99f35-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="99f35-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
