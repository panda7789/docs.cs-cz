---
title: ICorProfilerCallback::RuntimeResumeStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b163d41280c8ea49554cecb845c4be757f55dfc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168087"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="8bf6e-102">ICorProfilerCallback::RuntimeResumeStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="8bf6e-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="8bf6e-103">Oznámí profileru, že modul runtime obnovuje všemi vlákny za běhu.</span><span class="sxs-lookup"><span data-stu-id="8bf6e-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bf6e-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8bf6e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bf6e-105">Requirements</span></span>  
 <span data-ttu-id="8bf6e-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf6e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf6e-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bf6e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bf6e-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bf6e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bf6e-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf6e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf6e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bf6e-110">See also</span></span>

- [<span data-ttu-id="8bf6e-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bf6e-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8bf6e-112">RuntimeResumeFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="8bf6e-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
