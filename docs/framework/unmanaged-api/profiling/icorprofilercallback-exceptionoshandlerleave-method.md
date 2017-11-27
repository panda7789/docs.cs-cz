---
title: "ICorProfilerCallback::ExceptionOSHandlerLeave – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98596fd640437639ee3d5ffad4bce8503f5f5e44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="54f7b-102">ICorProfilerCallback::ExceptionOSHandlerLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="54f7b-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="54f7b-103">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="54f7b-103">Not implemented.</span></span> <span data-ttu-id="54f7b-104">Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="54f7b-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f7b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54f7b-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="54f7b-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54f7b-106">Requirements</span></span>  
 <span data-ttu-id="54f7b-107">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54f7b-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f7b-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54f7b-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54f7b-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54f7b-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54f7b-110">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54f7b-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f7b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="54f7b-111">See Also</span></span>  
 [<span data-ttu-id="54f7b-112">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54f7b-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
