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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a45c757a9176c77c7dbf58333b66d9b26514265
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471209"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="9aa73-102">ICorProfilerCallback::AssemblyUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9aa73-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="9aa73-103">Oznámí profileru, že je sestavení uvolňován.</span><span class="sxs-lookup"><span data-stu-id="9aa73-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aa73-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aa73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aa73-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="9aa73-106">[in] Určuje sestavení, které uvolňován.</span><span class="sxs-lookup"><span data-stu-id="9aa73-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aa73-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9aa73-107">Remarks</span></span>  
 <span data-ttu-id="9aa73-108">Hodnota `assemblyId` není platná pro požadavek informace po `AssemblyUnloadStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru a získat informace o tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="9aa73-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa73-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9aa73-109">Requirements</span></span>  
 <span data-ttu-id="9aa73-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aa73-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa73-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9aa73-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9aa73-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9aa73-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aa73-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa73-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa73-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9aa73-114">See also</span></span>
- [<span data-ttu-id="9aa73-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9aa73-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9aa73-116">AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="9aa73-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
