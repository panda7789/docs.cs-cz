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
ms.openlocfilehash: dcb2af2507306b22da14c13a42e4019261c8fa8c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866439"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="a3996-102">ICorProfilerCallback::ExceptionOSHandlerLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="a3996-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="a3996-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="a3996-103">Not implemented.</span></span> <span data-ttu-id="a3996-104">Profiler, který potřebuje informace o nespravovaných výjimkách, musí tyto informace získat jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a3996-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3996-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3996-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a3996-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3996-106">Requirements</span></span>  
 <span data-ttu-id="a3996-107">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3996-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3996-108">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3996-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3996-109">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3996-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3996-110">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3996-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3996-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3996-111">See also</span></span>

- [<span data-ttu-id="a3996-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3996-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
