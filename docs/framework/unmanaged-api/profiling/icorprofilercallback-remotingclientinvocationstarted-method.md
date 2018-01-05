---
title: "ICorProfilerCallback::RemotingClientInvocationStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 071e2892202271cac5e0acb226e9bef0e626b134
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="01b13-102">ICorProfilerCallback::RemotingClientInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="01b13-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="01b13-103">Aby bylo zahájeno vzdáleného volání upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="01b13-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01b13-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="01b13-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01b13-105">Remarks</span></span>  
 <span data-ttu-id="01b13-106">Tato událost je stejný pro synchronní a asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="01b13-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="01b13-107">Každé z následujících dvojic zpětných volání dojde ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="01b13-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="01b13-108">`RemotingClientInvocationStarted`a [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="01b13-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="01b13-109">[Icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [icorprofilercallback::remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="01b13-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="01b13-110">[Icorprofilercallback::remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="01b13-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="01b13-111">Je třeba si uvědomit následující problémů s zpětná volání vzdálenou komunikaci:</span><span class="sxs-lookup"><span data-stu-id="01b13-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="01b13-112">Spuštění funkce vzdálené komunikace není odráží profileru rozhraní API, takže nejsou správně přijata žádná oznámení pro funkce, které jsou vyvolávány z klienta a spuštěny na serveru.</span><span class="sxs-lookup"><span data-stu-id="01b13-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="01b13-113">Skutečné volání se stane prostřednictvím objekt proxy serveru; k profileru zdá se, že určité funkce jsou, ale nikdy použité kompilována.</span><span class="sxs-lookup"><span data-stu-id="01b13-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="01b13-114">Profileru neobdrží přesné oznámení pro asynchronní vzdálené komunikace události.</span><span class="sxs-lookup"><span data-stu-id="01b13-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b13-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01b13-115">Requirements</span></span>  
 <span data-ttu-id="01b13-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b13-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b13-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01b13-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01b13-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01b13-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01b13-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b13-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b13-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="01b13-120">See Also</span></span>  
 [<span data-ttu-id="01b13-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01b13-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
