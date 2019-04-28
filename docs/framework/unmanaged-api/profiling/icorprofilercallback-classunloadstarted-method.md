---
title: ICorProfilerCallback::ClassUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0707351d28ef75083b7bfb6ded38bc2a8460131
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597580"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="628ba-102">ICorProfilerCallback::ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="628ba-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="628ba-103">Oznámí profileru, že třída uvolňován.</span><span class="sxs-lookup"><span data-stu-id="628ba-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="628ba-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="628ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="628ba-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="628ba-106">[in] Určuje třídu, která uvolňován.</span><span class="sxs-lookup"><span data-stu-id="628ba-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="628ba-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="628ba-107">Remarks</span></span>  
 <span data-ttu-id="628ba-108">Hodnota `classId` není platná pro požadavek informace po `ClassUnloadStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru získat informace o této třídy.</span><span class="sxs-lookup"><span data-stu-id="628ba-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="628ba-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="628ba-109">Requirements</span></span>  
 <span data-ttu-id="628ba-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="628ba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="628ba-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="628ba-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="628ba-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="628ba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="628ba-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="628ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628ba-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="628ba-114">See also</span></span>

- [<span data-ttu-id="628ba-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="628ba-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="628ba-116">ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="628ba-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
