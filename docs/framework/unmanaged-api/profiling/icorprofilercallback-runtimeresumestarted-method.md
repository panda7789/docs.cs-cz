---
title: "ICorProfilerCallback::RuntimeResumeStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeResumeStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7949d742044eeffca2a35ffec790a7f91c418076
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="5e22e-102">ICorProfilerCallback::RuntimeResumeStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="5e22e-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="5e22e-103">Upozorní profileru, že modul runtime obnovuje všechna vlákna běhu.</span><span class="sxs-lookup"><span data-stu-id="5e22e-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e22e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e22e-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e22e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e22e-105">Requirements</span></span>  
 <span data-ttu-id="5e22e-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e22e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e22e-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e22e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e22e-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e22e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e22e-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e22e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e22e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e22e-110">See Also</span></span>  
 [<span data-ttu-id="5e22e-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e22e-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5e22e-112">RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="5e22e-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
