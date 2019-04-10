---
title: ICorProfilerCallback::RemotingServerInvocationStarted – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c9a4aa165057f1345de2c6f5bda80e4317d06c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221805"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="7de09-102">ICorProfilerCallback::RemotingServerInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="7de09-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="7de09-103">Oznámí profileru, že proces je volání metody v reakci na žádost o vzdálené metody volání.</span><span class="sxs-lookup"><span data-stu-id="7de09-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7de09-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="7de09-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7de09-105">Requirements</span></span>  
 <span data-ttu-id="7de09-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7de09-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7de09-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7de09-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7de09-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7de09-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7de09-109">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7de09-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7de09-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7de09-110">See also</span></span>

- [<span data-ttu-id="7de09-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7de09-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
