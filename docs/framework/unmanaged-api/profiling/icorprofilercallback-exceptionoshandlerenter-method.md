---
title: "ICorProfilerCallback::ExceptionOSHandlerEnter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c26260a2f70537deefb5600c0b721e0c0faf0399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="cb777-102">ICorProfilerCallback::ExceptionOSHandlerEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="cb777-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="cb777-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="cb777-103">Not implemented.</span></span> <span data-ttu-id="cb777-104">Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="cb777-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb777-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb777-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="cb777-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb777-106">Requirements</span></span>  
 <span data-ttu-id="cb777-107">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb777-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb777-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb777-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb777-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb777-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb777-110">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb777-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb777-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb777-111">See Also</span></span>  
 [<span data-ttu-id="cb777-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb777-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
