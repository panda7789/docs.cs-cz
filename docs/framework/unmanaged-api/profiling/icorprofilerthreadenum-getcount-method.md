---
title: ICorProfilerThreadEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 230b02b71abea48b1c3ad4094ea90812493149d1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860992"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="e7c60-102">ICorProfilerThreadEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="e7c60-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="e7c60-103">Získá počet vláken, která aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="e7c60-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7c60-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7c60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7c60-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e7c60-106">mimo Počet vláken, která aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="e7c60-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c60-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7c60-107">Requirements</span></span>  
 <span data-ttu-id="e7c60-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7c60-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c60-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e7c60-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7c60-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e7c60-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7c60-111">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7c60-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c60-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7c60-112">See also</span></span>

- [<span data-ttu-id="e7c60-113">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7c60-113">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="e7c60-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e7c60-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
