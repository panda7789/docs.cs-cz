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
ms.openlocfilehash: 01404d23707be90b6b15cf741632400d49f164de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445147"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="2db63-102">ICorProfilerCallback::AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="2db63-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="2db63-103">Upozorní profileru, že bylo sestavení uvolněno.</span><span class="sxs-lookup"><span data-stu-id="2db63-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2db63-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2db63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2db63-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="2db63-106">pro Identifikuje sestavení, které je uvolňováno.</span><span class="sxs-lookup"><span data-stu-id="2db63-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2db63-107">pro Hodnota HRESULT, která označuje, zda bylo sestavení uvolněno úspěšně.</span><span class="sxs-lookup"><span data-stu-id="2db63-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2db63-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2db63-108">Remarks</span></span>  
 <span data-ttu-id="2db63-109">Hodnota `assemblyId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: assemblyunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2db63-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="2db63-110">Některé části uvolňování sestavení mohou pokračovat po `AssemblyUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2db63-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="2db63-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="2db63-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2db63-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část uvolňování sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="2db63-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2db63-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2db63-113">Requirements</span></span>  
 <span data-ttu-id="2db63-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2db63-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2db63-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2db63-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2db63-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2db63-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2db63-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2db63-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db63-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2db63-118">See also</span></span>

- [<span data-ttu-id="2db63-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2db63-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
