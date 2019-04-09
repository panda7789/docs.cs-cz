---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdea3b0cc5b21cd881fe0ff3e0278444a22d083d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117193"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="d5f80-102">ICorProfilerCallback::ExceptionSearchFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="d5f80-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="d5f80-103">Oznámí profileru, že hledání fáze zpracování výjimek dokončil vyhledávání funkce.</span><span class="sxs-lookup"><span data-stu-id="d5f80-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5f80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5f80-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d5f80-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5f80-105">Requirements</span></span>  
 <span data-ttu-id="d5f80-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5f80-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f80-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5f80-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5f80-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5f80-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d5f80-109">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d5f80-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5f80-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5f80-110">See also</span></span>

- [<span data-ttu-id="d5f80-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5f80-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d5f80-112">ExceptionSearchFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="d5f80-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
