---
title: ICorProfilerCallback::ClassLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 5b465216da39e8cf207f0614519720453c384ae9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866582"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="38461-102">ICorProfilerCallback::ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="38461-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="38461-103">Upozorní profileru, že je načtena třída.</span><span class="sxs-lookup"><span data-stu-id="38461-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38461-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38461-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38461-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38461-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="38461-106">\[v] identifikuje třídu, která se načítá.</span><span class="sxs-lookup"><span data-stu-id="38461-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="38461-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38461-107">Remarks</span></span>  
 <span data-ttu-id="38461-108">Hodnota `classId` není platná pro požadavek na informace, dokud není volána metoda [ICorProfilerCallback:: ClassLoadFinished –](icorprofilercallback-classloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="38461-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38461-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38461-109">Requirements</span></span>  
 <span data-ttu-id="38461-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38461-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38461-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="38461-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38461-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38461-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38461-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38461-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38461-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38461-114">See also</span></span>

- [<span data-ttu-id="38461-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38461-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
