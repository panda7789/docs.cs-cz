---
title: ICorProfilerFunctionEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 137b1da853535985b2fd383d52f0bcfc48f728ed
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503091"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="303f5-102">ICorProfilerFunctionEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="303f5-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="303f5-103">Získá počet funkcí, které byly načteny aplikací nebo vynuceně načteny profilerem.</span><span class="sxs-lookup"><span data-stu-id="303f5-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="303f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="303f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="303f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="303f5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="303f5-106">mimo Počet načtených funkcí.</span><span class="sxs-lookup"><span data-stu-id="303f5-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="303f5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="303f5-107">Requirements</span></span>  
 <span data-ttu-id="303f5-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="303f5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="303f5-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="303f5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="303f5-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="303f5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="303f5-111">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="303f5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303f5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="303f5-112">See also</span></span>

- [<span data-ttu-id="303f5-113">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="303f5-113">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="303f5-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="303f5-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
