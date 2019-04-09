---
title: ICorProfilerCallback::ExceptionSearchFilterEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be91772f07e1a06c7df5b16fd70812e6a522d736
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192586"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="e7836-102">ICorProfilerCallback::ExceptionSearchFilterEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="e7836-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="e7836-103">Oznámí profileru, že byl zahájen hledání fáze zpracování výjimek spouští filtr výjimek definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e7836-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7836-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7836-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7836-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7836-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e7836-106">[in] ID funkce, která obsahuje filtr.</span><span class="sxs-lookup"><span data-stu-id="e7836-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7836-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7836-107">Requirements</span></span>  
 <span data-ttu-id="e7836-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7836-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7836-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7836-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7836-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7836-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e7836-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e7836-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7836-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7836-112">See also</span></span>

- [<span data-ttu-id="e7836-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7836-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e7836-114">ExceptionSearchFilterLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="e7836-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
