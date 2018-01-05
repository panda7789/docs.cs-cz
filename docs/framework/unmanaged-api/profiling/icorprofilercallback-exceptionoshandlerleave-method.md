---
title: "ICorProfilerCallback::ExceptionOSHandlerLeave – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b42902ceb6210d1189f600f61ef703d9b2029893
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="f1aae-102">ICorProfilerCallback::ExceptionOSHandlerLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="f1aae-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="f1aae-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="f1aae-103">Not implemented.</span></span> <span data-ttu-id="f1aae-104">Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f1aae-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1aae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1aae-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f1aae-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1aae-106">Requirements</span></span>  
 <span data-ttu-id="f1aae-107">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1aae-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1aae-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1aae-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1aae-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1aae-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1aae-110">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1aae-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1aae-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1aae-111">See Also</span></span>  
 [<span data-ttu-id="f1aae-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1aae-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
