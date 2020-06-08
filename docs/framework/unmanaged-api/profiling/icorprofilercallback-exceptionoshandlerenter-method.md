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
ms.openlocfilehash: c2c9ed848984d36ddf10d32d120deda76a4d47cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500283"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="808e5-102">ICorProfilerCallback::ExceptionOSHandlerEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="808e5-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="808e5-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="808e5-103">Not implemented.</span></span> <span data-ttu-id="808e5-104">Profiler, který potřebuje informace o nespravovaných výjimkách, musí tyto informace získat jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="808e5-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="808e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="808e5-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="808e5-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="808e5-106">Requirements</span></span>  
 <span data-ttu-id="808e5-107">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="808e5-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="808e5-108">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="808e5-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="808e5-109">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="808e5-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="808e5-110">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="808e5-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808e5-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="808e5-111">See also</span></span>

- [<span data-ttu-id="808e5-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="808e5-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
