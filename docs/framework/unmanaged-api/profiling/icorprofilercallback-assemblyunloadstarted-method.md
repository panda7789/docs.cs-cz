---
title: ICorProfilerCallback::AssemblyUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 3abf944df3619256791882bf61dfc4072b642c54
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445140"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="1bd39-102">ICorProfilerCallback::AssemblyUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="1bd39-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="1bd39-103">Upozorní profileru, že probíhá uvolňování sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bd39-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bd39-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bd39-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="1bd39-106">pro Identifikuje sestavení, které je uvolňováno.</span><span class="sxs-lookup"><span data-stu-id="1bd39-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bd39-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bd39-107">Remarks</span></span>  
 <span data-ttu-id="1bd39-108">Hodnota `assemblyId` není platná pro požadavek na informace po návratu metody `AssemblyUnloadStarted` – jedná se o poslední možnost profileru k získání informací o tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bd39-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd39-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bd39-109">Requirements</span></span>  
 <span data-ttu-id="1bd39-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd39-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd39-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1bd39-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bd39-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1bd39-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd39-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd39-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd39-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bd39-114">See also</span></span>

- [<span data-ttu-id="1bd39-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1bd39-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1bd39-116">AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="1bd39-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
