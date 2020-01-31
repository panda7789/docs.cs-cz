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
ms.openlocfilehash: 93bd1010374413f3f4ef7e1424ff8194dded8bb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866042"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="ca5c9-102">ICorProfilerCallback::RemotingClientInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ca5c9-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="ca5c9-103">Upozorní profileru, že bylo zahájeno volání vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca5c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca5c9-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ca5c9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca5c9-105">Remarks</span></span>  
 <span data-ttu-id="ca5c9-106">Tato událost je stejná pro synchronní a asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="ca5c9-107">Každý z následujících dvojic zpětných volání bude proveden ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="ca5c9-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="ca5c9-108">`RemotingClientInvocationStarted` a [ICorProfilerCallback:: remotingclientsendingmessage –](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="ca5c9-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="ca5c9-109">[ICorProfilerCallback:: remotingclientreceivingreply –](icorprofilercallback-remotingclientreceivingreply-method.md) a [ICorProfilerCallback:: remotingclientinvocationfinished –](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="ca5c9-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="ca5c9-110">[ICorProfilerCallback:: remotingserverinvocationreturned –](icorprofilercallback-remotingserverinvocationreturned-method.md) a [ICorProfilerCallback:: remotingserversendingreply –](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="ca5c9-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="ca5c9-111">Při zpětném volání vzdálené komunikace byste měli mít na paměti tyto problémy:</span><span class="sxs-lookup"><span data-stu-id="ca5c9-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="ca5c9-112">Spuštění funkce vzdálené komunikace se neprojeví v rozhraní API profileru, takže oznámení funkcí volaných z klienta a prováděná na serveru nejsou správně přijatá.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="ca5c9-113">Ke skutečnému vyvolání dojde prostřednictvím objektu proxy; do profileru se zobrazí, že některé funkce jsou kompilovány JIT, ale nikdy se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="ca5c9-114">Profiler neobdrží přesná upozornění na asynchronní události vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca5c9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca5c9-115">Requirements</span></span>  
 <span data-ttu-id="ca5c9-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca5c9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca5c9-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ca5c9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca5c9-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ca5c9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca5c9-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca5c9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca5c9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca5c9-120">See also</span></span>

- [<span data-ttu-id="ca5c9-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca5c9-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
