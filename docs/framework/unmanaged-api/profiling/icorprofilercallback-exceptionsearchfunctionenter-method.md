---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0615f37d97359f73eb1277da174b7e6401bfc313
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500340"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="78cf2-102">ICorProfilerCallback::ExceptionSearchFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="78cf2-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="78cf2-103">Oznámí profileru, že byl zahájen hledání fáze zpracování výjimek hledání funkce k vyhledání obslužnou rutinu pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="78cf2-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78cf2-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78cf2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78cf2-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="78cf2-106">[in] ID funkce, která byla zadána.</span><span class="sxs-lookup"><span data-stu-id="78cf2-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cf2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78cf2-107">Requirements</span></span>  
 <span data-ttu-id="78cf2-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cf2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cf2-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78cf2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78cf2-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78cf2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78cf2-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cf2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cf2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78cf2-112">See also</span></span>
- [<span data-ttu-id="78cf2-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78cf2-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="78cf2-114">ExceptionSearchFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="78cf2-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
