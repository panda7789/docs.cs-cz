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
ms.openlocfilehash: f5786db1f17e8a463dc78f9c93464145be3a8f32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499984"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="bd1c7-102">ICorProfilerCallback::RemotingClientInvocationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="bd1c7-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="bd1c7-103">Upozorní profileru, že volání vzdálené komunikace bylo dokončeno na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd1c7-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd1c7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd1c7-105">Remarks</span></span>  
 <span data-ttu-id="bd1c7-106">Pokud bylo volání vzdálené komunikace synchronní, bylo spuštěno také dokončení na serveru.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="bd1c7-107">Pokud bylo volání vzdálené komunikace asynchronní, může být při zpracování volání stále očekávána odpověď.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="bd1c7-108">Pokud je očekávána odpověď, bude provedena jako volání metody [ICorProfilerCallback:: remotingclientreceivingreply –](icorprofilercallback-remotingclientreceivingreply-method.md) a další volání k `RemotingClientInvocationFinished` Určení požadovaného sekundárního zpracování asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="bd1c7-109">Každý z následujících dvojic zpětných volání bude proveden ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="bd1c7-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="bd1c7-110">`RemotingClientInvocationStarted`a [ICorProfilerCallback:: remotingclientsendingmessage –](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="bd1c7-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="bd1c7-111">[ICorProfilerCallback:: remotingclientreceivingreply –](icorprofilercallback-remotingclientreceivingreply-method.md) a [ICorProfilerCallback:: remotingclientinvocationfinished –](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="bd1c7-111">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="bd1c7-112">[ICorProfilerCallback:: remotingserverinvocationreturned –](icorprofilercallback-remotingserverinvocationreturned-method.md) a [ICorProfilerCallback:: remotingserversendingreply –](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="bd1c7-112">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="bd1c7-113">Při zpětném volání vzdálené komunikace byste měli mít na paměti tyto problémy:</span><span class="sxs-lookup"><span data-stu-id="bd1c7-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="bd1c7-114">Spuštění funkce vzdálené komunikace se neprojeví v rozhraní API profileru, takže oznámení funkcí volaných z klienta a prováděná na serveru nejsou správně přijatá.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="bd1c7-115">Ke skutečnému vyvolání dojde prostřednictvím objektu proxy; do profileru se zobrazí, že některé funkce jsou kompilovány JIT, ale nikdy se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="bd1c7-116">Profiler neobdrží přesná upozornění na asynchronní události vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd1c7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd1c7-117">Requirements</span></span>  
 <span data-ttu-id="bd1c7-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd1c7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1c7-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd1c7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd1c7-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bd1c7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd1c7-121">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1c7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd1c7-122">See also</span></span>

- [<span data-ttu-id="bd1c7-123">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd1c7-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
