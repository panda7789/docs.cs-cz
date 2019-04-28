---
title: ICorProfilerCallback::ExceptionSearchFilterLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e89b76f7a246277737123e180c20874940437506
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597501"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="545f5-102">ICorProfilerCallback::ExceptionSearchFilterLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="545f5-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="545f5-103">Oznámí profileru, že filtr uživatelů jenom neskončí.</span><span class="sxs-lookup"><span data-stu-id="545f5-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="545f5-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="545f5-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="545f5-105">Requirements</span></span>  
 <span data-ttu-id="545f5-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="545f5-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545f5-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="545f5-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="545f5-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="545f5-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="545f5-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545f5-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545f5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="545f5-110">See also</span></span>

- [<span data-ttu-id="545f5-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="545f5-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="545f5-112">ExceptionSearchFilterEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="545f5-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
