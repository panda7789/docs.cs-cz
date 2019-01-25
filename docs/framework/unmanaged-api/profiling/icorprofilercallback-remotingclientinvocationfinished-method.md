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
ms.openlocfilehash: dddaaea2421de9c63d5d45f7add85b5da3019aee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696487"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="6dc76-102">ICorProfilerCallback::RemotingClientInvocationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6dc76-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="6dc76-103">Oznámí profileru, že dokončení běh vzdálené volání na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="6dc76-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dc76-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6dc76-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dc76-105">Remarks</span></span>  
 <span data-ttu-id="6dc76-106">Pokud se vzdáleným voláním synchronní, ji má také spustit dokončení na serveru.</span><span class="sxs-lookup"><span data-stu-id="6dc76-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="6dc76-107">Pokud bylo vzdálené volání asynchronní, odpověď může stále očekávat při zpracování volání.</span><span class="sxs-lookup"><span data-stu-id="6dc76-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="6dc76-108">Pokud se očekává odpověď, tato hodnota se vrátí jako volání [icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a další volání `RemotingClientInvocationFinished` udávajících vyžaduje sekundární zpracování asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="6dc76-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="6dc76-109">Každé z následujících dvojic zpětná volání dojde ve stejném vlákně:</span><span class="sxs-lookup"><span data-stu-id="6dc76-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="6dc76-110">`RemotingClientInvocationStarted` a [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="6dc76-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="6dc76-111">[Icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) a [icorprofilercallback::remotingclientinvocationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="6dc76-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="6dc76-112">[Icorprofilercallback::remotingserverinvocationreturned –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) a [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="6dc76-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="6dc76-113">Byste měli vědět o následujících potíží u vzdálené komunikace zpětná volání:</span><span class="sxs-lookup"><span data-stu-id="6dc76-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="6dc76-114">Provedení funkce vzdálené komunikace se neprojeví v Profilování rozhraní API, proto nejsou správně zasílána oznámení pro funkce, které jsou vyvolávány z klienta a spuštěny na serveru.</span><span class="sxs-lookup"><span data-stu-id="6dc76-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="6dc76-115">Skutečné vyvolání se stane přes proxy server objektu. k profileru zdá se, že některé funkce jsou sestaveny JIT, ale nikdy použité.</span><span class="sxs-lookup"><span data-stu-id="6dc76-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="6dc76-116">Profiler nezíská přesné oznámení o události asynchronní vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="6dc76-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dc76-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dc76-117">Requirements</span></span>  
 <span data-ttu-id="6dc76-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dc76-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dc76-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dc76-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dc76-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dc76-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dc76-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dc76-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc76-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dc76-122">See also</span></span>
- [<span data-ttu-id="6dc76-123">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6dc76-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
