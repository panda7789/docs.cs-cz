---
title: ICorProfilerInfo4::EnumThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: 5bea1b75e94d8011d3582d4f07d36bbc7a560502
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862214"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="059be-102">ICorProfilerInfo4::EnumThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="059be-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="059be-103">Vrátí enumerátor, který poskytuje metody pro sekvenční iteraci v kolekci všech spravovaných vláken v profilované procesu.</span><span class="sxs-lookup"><span data-stu-id="059be-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="059be-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="059be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="059be-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="059be-106">mimo Ukazatel na rozhraní [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="059be-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="059be-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="059be-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="059be-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="059be-108">Requirements</span></span>  
 <span data-ttu-id="059be-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="059be-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="059be-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="059be-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="059be-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="059be-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="059be-112">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="059be-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059be-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="059be-113">See also</span></span>

- [<span data-ttu-id="059be-114">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="059be-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="059be-115">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="059be-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="059be-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="059be-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="059be-117">Profilace</span><span class="sxs-lookup"><span data-stu-id="059be-117">Profiling</span></span>](index.md)
