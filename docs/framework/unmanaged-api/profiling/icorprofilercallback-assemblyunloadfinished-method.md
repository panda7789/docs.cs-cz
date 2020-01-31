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
ms.openlocfilehash: 734ae1d14d02d47c7d3126f1b4cf55dcb4ad151b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866621"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="9953b-102">ICorProfilerCallback::AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="9953b-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="9953b-103">Upozorní profileru, že bylo sestavení uvolněno.</span><span class="sxs-lookup"><span data-stu-id="9953b-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9953b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9953b-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9953b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9953b-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="9953b-106">\[v] identifikuje sestavení, které se uvolní.</span><span class="sxs-lookup"><span data-stu-id="9953b-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="9953b-107">\[in] hodnota HRESULT, která označuje, zda bylo sestavení uvolněno úspěšně.</span><span class="sxs-lookup"><span data-stu-id="9953b-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="9953b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9953b-108">Remarks</span></span>  
 <span data-ttu-id="9953b-109">Hodnota `assemblyId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: assemblyunloadstarted –](icorprofilercallback-assemblyunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9953b-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="9953b-110">Některé části uvolňování sestavení mohou pokračovat po `AssemblyUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9953b-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="9953b-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="9953b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9953b-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část uvolňování sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9953b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9953b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9953b-113">Requirements</span></span>  
 <span data-ttu-id="9953b-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9953b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9953b-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9953b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9953b-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9953b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9953b-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9953b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9953b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9953b-118">See also</span></span>

- [<span data-ttu-id="9953b-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9953b-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
