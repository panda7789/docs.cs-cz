---
title: ICorProfilerCallback::RemotingClientInvocationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec45b73b496efdbe6328985b5f77f731d8a78cc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453402"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="c6ced-102">ICorProfilerCallback::RemotingClientInvocationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c6ced-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="c6ced-103">Jestli volání vzdálené komunikace spustila dokončení v klientském počítači upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="c6ced-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ced-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ced-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c6ced-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6ced-105">Remarks</span></span>  
 <span data-ttu-id="c6ced-106">Pokud bylo synchronní volání vzdálenou komunikaci, je spuštěn také na dokončení na serveru.</span><span class="sxs-lookup"><span data-stu-id="c6ced-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="c6ced-107">Pokud bylo asynchronní volání vzdálenou komunikaci, může při zpracování volání očekávané stále odpověď.</span><span class="sxs-lookup"><span data-stu-id="c6ced-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="c6ced-108">Pokud je odpověď očekávána, se vyskytnou během volání [icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a další volání `RemotingClientInvocationFinished` udávajících požadované sekundární zpracování asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="c6ced-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="c6ced-109">Každé z následujících dvojic zpětných volání dojde ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="c6ced-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="c6ced-110">`RemotingClientInvocationStarted` a [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="c6ced-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="c6ced-111">[Icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [icorprofilercallback::remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="c6ced-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="c6ced-112">[Icorprofilercallback::remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="c6ced-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="c6ced-113">Je třeba si uvědomit následující problémů s zpětná volání vzdálenou komunikaci:</span><span class="sxs-lookup"><span data-stu-id="c6ced-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="c6ced-114">Spuštění funkce vzdálené komunikace není odráží profileru rozhraní API, takže nejsou správně přijata žádná oznámení pro funkce, které jsou vyvolávány z klienta a spuštěny na serveru.</span><span class="sxs-lookup"><span data-stu-id="c6ced-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="c6ced-115">Skutečné volání se stane prostřednictvím objekt proxy serveru; k profileru zdá se, že určité funkce jsou, ale nikdy použité kompilována.</span><span class="sxs-lookup"><span data-stu-id="c6ced-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="c6ced-116">Profileru neobdrží přesné oznámení pro asynchronní vzdálené komunikace události.</span><span class="sxs-lookup"><span data-stu-id="c6ced-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ced-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6ced-117">Requirements</span></span>  
 <span data-ttu-id="c6ced-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ced-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ced-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6ced-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6ced-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6ced-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6ced-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ced-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ced-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6ced-122">See Also</span></span>  
 [<span data-ttu-id="c6ced-123">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6ced-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
