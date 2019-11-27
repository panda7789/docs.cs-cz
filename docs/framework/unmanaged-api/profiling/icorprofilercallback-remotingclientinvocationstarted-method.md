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
ms.openlocfilehash: 5de291774f1e20b4c399c416f9f52657fa8a9a84
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445822"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="bcc28-102">ICorProfilerCallback::RemotingClientInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="bcc28-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="bcc28-103">Upozorní profileru, že bylo zahájeno volání vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="bcc28-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcc28-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bcc28-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcc28-105">Remarks</span></span>  
 <span data-ttu-id="bcc28-106">Tato událost je stejná pro synchronní a asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="bcc28-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="bcc28-107">Každý z následujících dvojic zpětných volání bude proveden ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="bcc28-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="bcc28-108">`RemotingClientInvocationStarted` a [ICorProfilerCallback:: remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="bcc28-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="bcc28-109">[ICorProfilerCallback:: remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [ICorProfilerCallback:: remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="bcc28-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="bcc28-110">[ICorProfilerCallback:: remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [ICorProfilerCallback:: remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="bcc28-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="bcc28-111">Při zpětném volání vzdálené komunikace byste měli mít na paměti tyto problémy:</span><span class="sxs-lookup"><span data-stu-id="bcc28-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="bcc28-112">Spuštění funkce vzdálené komunikace se neprojeví v rozhraní API profileru, takže oznámení funkcí volaných z klienta a prováděná na serveru nejsou správně přijatá.</span><span class="sxs-lookup"><span data-stu-id="bcc28-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="bcc28-113">Ke skutečnému vyvolání dojde prostřednictvím objektu proxy; do profileru se zobrazí, že některé funkce jsou kompilovány JIT, ale nikdy se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="bcc28-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="bcc28-114">Profiler neobdrží přesná upozornění na asynchronní události vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="bcc28-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcc28-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcc28-115">Requirements</span></span>  
 <span data-ttu-id="bcc28-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc28-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc28-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bcc28-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcc28-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bcc28-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcc28-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcc28-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc28-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcc28-120">See also</span></span>

- [<span data-ttu-id="bcc28-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcc28-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
