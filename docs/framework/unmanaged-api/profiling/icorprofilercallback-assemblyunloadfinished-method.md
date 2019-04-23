---
title: ICorProfilerCallback::AssemblyUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ee87c926d2377ff8eef53f930fe75251b28ceb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137771"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="ff0a1-102">ICorProfilerCallback::AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ff0a1-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="ff0a1-103">Oznámí profileru, že sestavení byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff0a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff0a1-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff0a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff0a1-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="ff0a1-106">[in] Určuje sestavení, které uvolňován.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ff0a1-107">[in] HRESULT, která určuje, zda bylo sestavení úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff0a1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff0a1-108">Remarks</span></span>  
 <span data-ttu-id="ff0a1-109">Hodnota `assemblyId` není platná pro požadavek informace po [icorprofilercallback::assemblyunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="ff0a1-110">Některé části uvolňování sestavení může pokračovat po `AssemblyUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="ff0a1-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ff0a1-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolňování sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ff0a1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff0a1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff0a1-113">Requirements</span></span>  
 <span data-ttu-id="ff0a1-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff0a1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff0a1-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff0a1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff0a1-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff0a1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff0a1-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff0a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0a1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff0a1-118">See also</span></span>

- [<span data-ttu-id="ff0a1-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff0a1-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
