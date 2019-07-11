---
title: ICorProfilerCallback::ClassUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c1bf9e572ee88bd299f23ebb435c1b4d24ed717
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762929"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="9e2ff-102">ICorProfilerCallback::ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="9e2ff-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="9e2ff-103">Třída dokončení uvolnění oznámí profileru.</span><span class="sxs-lookup"><span data-stu-id="9e2ff-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e2ff-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e2ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e2ff-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9e2ff-106">[in] Určuje třídu, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="9e2ff-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="9e2ff-107">[in] HRESULT, která určuje, zda byla třída úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="9e2ff-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e2ff-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e2ff-108">Remarks</span></span>  
 <span data-ttu-id="9e2ff-109">Některé části uvolnění třídy může pokračovat po `ClassUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9e2ff-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="9e2ff-110">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="9e2ff-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9e2ff-111">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolnění třídy proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="9e2ff-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e2ff-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e2ff-112">Requirements</span></span>  
 <span data-ttu-id="9e2ff-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e2ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e2ff-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e2ff-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e2ff-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e2ff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e2ff-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e2ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2ff-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e2ff-117">See also</span></span>

- [<span data-ttu-id="9e2ff-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e2ff-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9e2ff-119">ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9e2ff-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
