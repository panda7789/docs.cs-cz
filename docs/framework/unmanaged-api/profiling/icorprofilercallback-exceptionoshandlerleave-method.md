---
title: ICorProfilerCallback::ExceptionOSHandlerLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0decfde08a9097c8fe5185c8b5a3fef4f7f68189
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213334"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="b983d-102">ICorProfilerCallback::ExceptionOSHandlerLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="b983d-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="b983d-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="b983d-103">Not implemented.</span></span> <span data-ttu-id="b983d-104">Profiler, který potřebuje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b983d-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b983d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b983d-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b983d-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b983d-106">Requirements</span></span>  
 <span data-ttu-id="b983d-107">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b983d-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b983d-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b983d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b983d-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b983d-109">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b983d-110">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b983d-110">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b983d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b983d-111">See also</span></span>

- [<span data-ttu-id="b983d-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b983d-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
