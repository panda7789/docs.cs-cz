---
title: "ICorProfilerCallback::RemotingServerInvocationStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0e2e2136b084f8dc1ea17001f4f6fff89adc575
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="d09a1-102">ICorProfilerCallback::RemotingServerInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="d09a1-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="d09a1-103">Upozorní profileru, že je proces vyvolání metody v reakci na žádost o volání vzdálené metody.</span><span class="sxs-lookup"><span data-stu-id="d09a1-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d09a1-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d09a1-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d09a1-105">Requirements</span></span>  
 <span data-ttu-id="d09a1-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09a1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09a1-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d09a1-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d09a1-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d09a1-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d09a1-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09a1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09a1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d09a1-110">See Also</span></span>  
 [<span data-ttu-id="d09a1-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d09a1-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
