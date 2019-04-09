---
title: ICorProfilerCallback::ExceptionOSHandlerEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fcdd52e648b2461036921772b6b5684ba6aec22
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175835"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="e45d3-102">ICorProfilerCallback::ExceptionOSHandlerEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="e45d3-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="e45d3-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="e45d3-103">Not implemented.</span></span> <span data-ttu-id="e45d3-104">Profiler, který potřebuje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="e45d3-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45d3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e45d3-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e45d3-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e45d3-106">Requirements</span></span>  
 <span data-ttu-id="e45d3-107">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e45d3-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e45d3-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e45d3-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e45d3-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e45d3-109">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e45d3-110">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e45d3-110">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e45d3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e45d3-111">See also</span></span>

- [<span data-ttu-id="e45d3-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e45d3-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
