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
ms.openlocfilehash: 920fa36edcc49c12f8f73644cc4e6551a0e954ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="53db0-102">ICorProfilerCallback::ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="53db0-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="53db0-103">Upozorní profileru, že byla dokončena třídu uvolnění.</span><span class="sxs-lookup"><span data-stu-id="53db0-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53db0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53db0-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53db0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53db0-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="53db0-106">[v] Určuje třídu, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="53db0-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="53db0-107">[v] HRESULT, která určuje, zda byla třída úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="53db0-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53db0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53db0-108">Remarks</span></span>  
 <span data-ttu-id="53db0-109">Některé části uvolnění třídy, může pokračovat i po `ClassUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="53db0-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="53db0-110">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="53db0-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="53db0-111">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění třídy proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="53db0-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53db0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53db0-112">Requirements</span></span>  
 <span data-ttu-id="53db0-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53db0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53db0-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53db0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53db0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53db0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53db0-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53db0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53db0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="53db0-117">See Also</span></span>  
 [<span data-ttu-id="53db0-118">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53db0-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="53db0-119">Classunloadstarted – metoda</span><span class="sxs-lookup"><span data-stu-id="53db0-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
