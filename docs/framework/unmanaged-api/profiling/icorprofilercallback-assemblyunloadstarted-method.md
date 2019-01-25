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
ms.openlocfilehash: 88ac588cd7eb98b4949aa993c66452de77dd100e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514726"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="d8a5e-102">ICorProfilerCallback::AssemblyUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="d8a5e-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="d8a5e-103">Oznámí profileru, že je sestavení uvolňován.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8a5e-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8a5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8a5e-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="d8a5e-106">[in] Určuje sestavení, které uvolňován.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8a5e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8a5e-107">Remarks</span></span>  
 <span data-ttu-id="d8a5e-108">Hodnota `assemblyId` není platná pro požadavek informace po `AssemblyUnloadStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru a získat informace o tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8a5e-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8a5e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8a5e-109">Requirements</span></span>  
 <span data-ttu-id="d8a5e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8a5e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8a5e-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8a5e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8a5e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8a5e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8a5e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8a5e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a5e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8a5e-114">See also</span></span>
- [<span data-ttu-id="d8a5e-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8a5e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d8a5e-116">AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="d8a5e-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
