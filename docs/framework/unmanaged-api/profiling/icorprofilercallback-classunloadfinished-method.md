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
ms.openlocfilehash: ebf72fe4f9fae5b3d791e6eed2e9421b9f4e3296
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450814"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="5e8d7-102">ICorProfilerCallback::ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="5e8d7-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="5e8d7-103">Upozorní profileru, že byla dokončena třídu uvolnění.</span><span class="sxs-lookup"><span data-stu-id="5e8d7-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e8d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e8d7-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e8d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e8d7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5e8d7-106">[v] Určuje třídu, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="5e8d7-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="5e8d7-107">[v] HRESULT, která určuje, zda byla třída úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="5e8d7-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e8d7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e8d7-108">Remarks</span></span>  
 <span data-ttu-id="5e8d7-109">Některé části uvolnění třídy, může pokračovat i po `ClassUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5e8d7-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="5e8d7-110">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="5e8d7-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="5e8d7-111">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění třídy proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5e8d7-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e8d7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e8d7-112">Requirements</span></span>  
 <span data-ttu-id="5e8d7-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e8d7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e8d7-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e8d7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e8d7-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e8d7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e8d7-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e8d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8d7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e8d7-117">See Also</span></span>  
 [<span data-ttu-id="5e8d7-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e8d7-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5e8d7-119">ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="5e8d7-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
