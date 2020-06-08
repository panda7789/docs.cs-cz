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
ms.openlocfilehash: 604ecb2122cce6e24f0e5168fa286a523d8bb4f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495070"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="7041a-102">ICorProfilerModuleEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7041a-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="7041a-103">Získá počet spravovaných modulů, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="7041a-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7041a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7041a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7041a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7041a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7041a-106">mimo Počet běhových modulů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7041a-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7041a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7041a-107">Requirements</span></span>  
 <span data-ttu-id="7041a-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7041a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7041a-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7041a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7041a-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7041a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7041a-111">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7041a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7041a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7041a-112">See also</span></span>

- [<span data-ttu-id="7041a-113">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7041a-113">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="7041a-114">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7041a-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
