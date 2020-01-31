---
title: ICorProfilerModuleEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: 772a7c08c934fda59a2764e1fbe22d3d2b08a620
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861499"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="7d215-102">ICorProfilerModuleEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7d215-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="7d215-103">Získá počet spravovaných modulů, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d215-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d215-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d215-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d215-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d215-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7d215-106">mimo Počet běhových modulů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7d215-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d215-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d215-107">Requirements</span></span>  
 <span data-ttu-id="7d215-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d215-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d215-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7d215-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d215-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d215-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d215-111">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d215-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d215-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d215-112">See also</span></span>

- [<span data-ttu-id="7d215-113">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d215-113">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="7d215-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7d215-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
