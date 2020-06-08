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
ms.openlocfilehash: ccbb051ac30fb25199ce12c16fff74bb0b9944fa
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495083"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="29516-102">ICorProfilerModuleEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="29516-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="29516-103">Získá ukazatel rozhraní na kopii tohoto rozhraní [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="29516-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29516-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29516-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29516-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29516-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="29516-106">mimo Ukazatel na ukazatel rozhraní, který zase odkazuje na kopii tohoto rozhraní [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="29516-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="29516-107">Kopie enumerátoru udržuje svůj vlastní stav výčtu odděleně od tohoto enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="29516-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="29516-108">Počáteční pozice kurzoru pro kopii je však stejná jako aktuální pozice kurzoru tohoto čítače.</span><span class="sxs-lookup"><span data-stu-id="29516-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29516-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29516-109">Requirements</span></span>  
 <span data-ttu-id="29516-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29516-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29516-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="29516-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29516-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29516-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29516-113">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29516-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29516-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29516-114">See also</span></span>

- [<span data-ttu-id="29516-115">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29516-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="29516-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="29516-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
