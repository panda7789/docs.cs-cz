---
title: "ICorProfilerCallback::ClassUnloadFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9801113e23474fa0aae461d356e4aa57a203bd6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="142eb-102">ICorProfilerCallback::ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="142eb-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="142eb-103">Upozorní profileru, že byla dokončena třídu uvolnění.</span><span class="sxs-lookup"><span data-stu-id="142eb-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="142eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="142eb-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="142eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="142eb-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="142eb-106">[v] Určuje třídu, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="142eb-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="142eb-107">[v] HRESULT, která určuje, zda byla třída úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="142eb-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="142eb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="142eb-108">Remarks</span></span>  
 <span data-ttu-id="142eb-109">Některé části uvolnění třídy, může pokračovat i po `ClassUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="142eb-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="142eb-110">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="142eb-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="142eb-111">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění třídy proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="142eb-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="142eb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="142eb-112">Requirements</span></span>  
 <span data-ttu-id="142eb-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="142eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="142eb-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="142eb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="142eb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="142eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="142eb-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="142eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142eb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="142eb-117">See Also</span></span>  
 [<span data-ttu-id="142eb-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="142eb-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="142eb-119">ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="142eb-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
