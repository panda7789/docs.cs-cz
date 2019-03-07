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
ms.openlocfilehash: 7ed5debad7ef6722206daac98aecd7db11155a58
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469284"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="029dc-102">ICorProfilerCallback::AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="029dc-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="029dc-103">Oznámí profileru, že sestavení byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="029dc-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="029dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="029dc-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="029dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="029dc-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="029dc-106">[in] Určuje sestavení, které uvolňován.</span><span class="sxs-lookup"><span data-stu-id="029dc-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="029dc-107">[in] HRESULT, která určuje, zda bylo sestavení úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="029dc-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="029dc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="029dc-108">Remarks</span></span>  
 <span data-ttu-id="029dc-109">Hodnota `assemblyId` není platná pro požadavek informace po [icorprofilercallback::assemblyunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="029dc-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="029dc-110">Některé části uvolňování sestavení může pokračovat po `AssemblyUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="029dc-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="029dc-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="029dc-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="029dc-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolňování sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="029dc-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="029dc-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="029dc-113">Requirements</span></span>  
 <span data-ttu-id="029dc-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="029dc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="029dc-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="029dc-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="029dc-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="029dc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="029dc-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="029dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029dc-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="029dc-118">See also</span></span>
- [<span data-ttu-id="029dc-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="029dc-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
