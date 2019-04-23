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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124641"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="04e64-102">ICorProfilerCallback::ExceptionSearchFilterLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="04e64-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="04e64-103">Oznámí profileru, že filtr uživatelů jenom neskončí.</span><span class="sxs-lookup"><span data-stu-id="04e64-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e64-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="04e64-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04e64-105">Requirements</span></span>  
 <span data-ttu-id="04e64-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e64-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e64-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04e64-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04e64-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04e64-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04e64-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e64-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e64-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04e64-110">See also</span></span>

- [<span data-ttu-id="04e64-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04e64-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="04e64-112">ExceptionSearchFilterEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="04e64-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
