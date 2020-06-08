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
ms.openlocfilehash: 80054a8292c69b957664cb3573b0a8694c7f9fd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500400"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="b4fb7-102">ICorProfilerCallback::AssemblyUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="b4fb7-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="b4fb7-103">Upozorní profileru, že probíhá uvolňování sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4fb7-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4fb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4fb7-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4fb7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4fb7-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="b4fb7-106">\[v] identifikuje sestavení, které je uvolněno.</span><span class="sxs-lookup"><span data-stu-id="b4fb7-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4fb7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4fb7-107">Remarks</span></span>  
 <span data-ttu-id="b4fb7-108">Hodnota `assemblyId` není platná pro žádost o informace po `AssemblyUnloadStarted` návratu metody – jedná se o poslední možnost profileru k získání informací o tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4fb7-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4fb7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4fb7-109">Requirements</span></span>  
 <span data-ttu-id="b4fb7-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4fb7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4fb7-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b4fb7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4fb7-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4fb7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4fb7-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4fb7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fb7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4fb7-114">See also</span></span>

- [<span data-ttu-id="b4fb7-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4fb7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b4fb7-116">AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="b4fb7-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
