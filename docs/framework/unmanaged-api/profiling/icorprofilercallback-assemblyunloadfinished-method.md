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
ms.openlocfilehash: d00e67d29921edc6b7487ceeb12aaa9e9f9bd0ac
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500413"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="1d4b1-102">ICorProfilerCallback::AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="1d4b1-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="1d4b1-103">Upozorní profileru, že bylo sestavení uvolněno.</span><span class="sxs-lookup"><span data-stu-id="1d4b1-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d4b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d4b1-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d4b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d4b1-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="1d4b1-106">\[v] identifikuje sestavení, které je uvolněno.</span><span class="sxs-lookup"><span data-stu-id="1d4b1-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="1d4b1-107">\[in] HRESULT, který označuje, zda bylo sestavení uvolněno úspěšně.</span><span class="sxs-lookup"><span data-stu-id="1d4b1-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d4b1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d4b1-108">Remarks</span></span>  
 <span data-ttu-id="1d4b1-109">Hodnota `assemblyId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: assemblyunloadstarted –](icorprofilercallback-assemblyunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1d4b1-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="1d4b1-110">Některé části uvolňování sestavení mohou pokračovat po `AssemblyUnloadFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="1d4b1-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="1d4b1-111">Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání.</span><span class="sxs-lookup"><span data-stu-id="1d4b1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="1d4b1-112">Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část uvolňování sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1d4b1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d4b1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d4b1-113">Requirements</span></span>  
 <span data-ttu-id="1d4b1-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d4b1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d4b1-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1d4b1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d4b1-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1d4b1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d4b1-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d4b1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4b1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d4b1-118">See also</span></span>

- [<span data-ttu-id="1d4b1-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d4b1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
