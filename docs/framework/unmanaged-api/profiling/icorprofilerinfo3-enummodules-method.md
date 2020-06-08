---
title: ICorProfilerInfo3::EnumModules – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 85adf2dbdbb8c02192a9017bc4f664274a08ee24
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496578"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="7f47c-102">ICorProfilerInfo3::EnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="7f47c-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="7f47c-103">Vrátí enumerátor, který poskytuje metody pro sekvenční iteraci pomocí kolekce spravovaných modulů, které jsou načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f47c-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f47c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f47c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f47c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f47c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="7f47c-106">mimo Ukazatel na rozhraní [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7f47c-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f47c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f47c-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f47c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f47c-108">Requirements</span></span>  
 <span data-ttu-id="7f47c-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f47c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f47c-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7f47c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f47c-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7f47c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f47c-112">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f47c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f47c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f47c-113">See also</span></span>

- [<span data-ttu-id="7f47c-114">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f47c-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="7f47c-115">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f47c-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7f47c-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7f47c-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7f47c-117">Profilace</span><span class="sxs-lookup"><span data-stu-id="7f47c-117">Profiling</span></span>](index.md)
