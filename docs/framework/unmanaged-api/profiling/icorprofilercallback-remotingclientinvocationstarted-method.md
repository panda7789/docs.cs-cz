---
title: ICorProfilerCallback::RemotingClientInvocationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b452cbfc5564d98b3770c2ed97f8453296f0fc13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992157"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="c62c9-102">ICorProfilerCallback::RemotingClientInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c62c9-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="c62c9-103">Oznámí profileru, vzdálené volání byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c62c9-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c62c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c62c9-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c62c9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c62c9-105">Remarks</span></span>  
 <span data-ttu-id="c62c9-106">Tato událost je stejný pro synchronní a asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="c62c9-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="c62c9-107">Každé z následujících dvojic zpětná volání dojde ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="c62c9-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="c62c9-108">`RemotingClientInvocationStarted` a [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="c62c9-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="c62c9-109">[Icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [icorprofilercallback::remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="c62c9-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="c62c9-110">[Icorprofilercallback::remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="c62c9-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="c62c9-111">Byste měli vědět o následujících potíží u vzdálené komunikace zpětná volání:</span><span class="sxs-lookup"><span data-stu-id="c62c9-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="c62c9-112">Provedení funkce vzdálené komunikace se neprojeví v Profilování rozhraní API, proto nejsou správně zasílána oznámení pro funkce, které jsou vyvolávány z klienta a spuštěny na serveru.</span><span class="sxs-lookup"><span data-stu-id="c62c9-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="c62c9-113">Skutečné vyvolání se stane přes proxy server objektu. k profileru zdá se, že některé funkce jsou sestaveny JIT, ale nikdy použité.</span><span class="sxs-lookup"><span data-stu-id="c62c9-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="c62c9-114">Profiler nezíská přesné oznámení o události asynchronní vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="c62c9-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c62c9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c62c9-115">Requirements</span></span>  
 <span data-ttu-id="c62c9-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c62c9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c62c9-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c62c9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c62c9-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c62c9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c62c9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c62c9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62c9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c62c9-120">See also</span></span>

- [<span data-ttu-id="c62c9-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c62c9-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
