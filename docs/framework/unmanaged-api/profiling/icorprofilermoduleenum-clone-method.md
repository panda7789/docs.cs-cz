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
ms.openlocfilehash: a6b36883ec0914426b4f4c937390c1622faead25
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868288"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="deda2-102">ICorProfilerModuleEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="deda2-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="deda2-103">Získá ukazatel rozhraní na kopii tohoto rozhraní [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="deda2-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deda2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="deda2-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deda2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="deda2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="deda2-106">mimo Ukazatel na ukazatel rozhraní, který zase odkazuje na kopii tohoto rozhraní [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="deda2-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="deda2-107">Kopie enumerátoru udržuje svůj vlastní stav výčtu odděleně od tohoto enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="deda2-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="deda2-108">Počáteční pozice kurzoru pro kopii je však stejná jako aktuální pozice kurzoru tohoto čítače.</span><span class="sxs-lookup"><span data-stu-id="deda2-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deda2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="deda2-109">Requirements</span></span>  
 <span data-ttu-id="deda2-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deda2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deda2-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="deda2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="deda2-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="deda2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deda2-113">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deda2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deda2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="deda2-114">See also</span></span>

- [<span data-ttu-id="deda2-115">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="deda2-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="deda2-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="deda2-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
