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
ms.openlocfilehash: 607143d7848534329a55a9caebdb6b9175b2749c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866413"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="d9b9c-102">ICorProfilerCallback::ExceptionSearchFilterLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="d9b9c-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="d9b9c-103">Upozorní profileru, že uživatel právě dokončil provádění filtru.</span><span class="sxs-lookup"><span data-stu-id="d9b9c-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9b9c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d9b9c-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9b9c-105">Requirements</span></span>  
 <span data-ttu-id="d9b9c-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9b9c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b9c-107">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d9b9c-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9b9c-108">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d9b9c-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9b9c-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b9c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b9c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9b9c-110">See also</span></span>

- [<span data-ttu-id="d9b9c-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9b9c-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d9b9c-112">ExceptionSearchFilterEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="d9b9c-112">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
