---
title: "ICorProfilerCallback::ClassUnloadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0056d97e7cf8286291292f27e942b7a846efb3f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="9ea4f-102">ICorProfilerCallback::ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9ea4f-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="9ea4f-103">Odpojení třídy upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="9ea4f-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea4f-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ea4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ea4f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9ea4f-106">[v] Určuje třídu, která odpojení.</span><span class="sxs-lookup"><span data-stu-id="9ea4f-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ea4f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ea4f-107">Remarks</span></span>  
 <span data-ttu-id="9ea4f-108">Hodnota `classId` není platná pro požadavek informace po `ClassUnloadStarted` metoda vrátí – Toto je poslední možnost okna profilování ke získání informací o této třídy.</span><span class="sxs-lookup"><span data-stu-id="9ea4f-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ea4f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ea4f-109">Requirements</span></span>  
 <span data-ttu-id="9ea4f-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ea4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ea4f-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ea4f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ea4f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ea4f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ea4f-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ea4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea4f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ea4f-114">See Also</span></span>  
 [<span data-ttu-id="9ea4f-115">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ea4f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9ea4f-116">Classunloadfinished – metoda</span><span class="sxs-lookup"><span data-stu-id="9ea4f-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
