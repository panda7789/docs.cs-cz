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
ms.openlocfilehash: 9d01f3d7485b19c076d9cd3e83aeccbcf5e728f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160703"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="f9722-102">ICorProfilerCallback::ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f9722-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="f9722-103">Třída dokončení uvolnění oznámí profileru.</span><span class="sxs-lookup"><span data-stu-id="f9722-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9722-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9722-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9722-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9722-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="f9722-106">[in] Určuje třídu, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="f9722-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f9722-107">[in] HRESULT, která určuje, zda byla třída úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="f9722-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9722-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9722-108">Remarks</span></span>  
 <span data-ttu-id="f9722-109">Některé části uvolnění třídy může pokračovat po `ClassUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f9722-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="f9722-110">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="f9722-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f9722-111">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolnění třídy proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="f9722-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9722-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9722-112">Requirements</span></span>  
 <span data-ttu-id="f9722-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9722-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9722-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9722-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9722-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9722-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f9722-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f9722-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9722-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9722-117">See also</span></span>

- [<span data-ttu-id="f9722-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9722-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f9722-119">ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f9722-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
