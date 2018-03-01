---
title: "ICorProfilerCallback::RemotingServerSendingReply – metoda"
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
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f8fa5a81231c8181e0d0257a1bbfdb4a1f0a7a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="fcd6d-102">ICorProfilerCallback::RemotingServerSendingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="fcd6d-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="fcd6d-103">Profileru upozorní, že proces dokončení zpracování požadavku volání vzdálené metody a má přenášet odpověď prostřednictvím kanálu.</span><span class="sxs-lookup"><span data-stu-id="fcd6d-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcd6d-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcd6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcd6d-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="fcd6d-106">[v] Ukazatel na identifikátor GUID, který bude odpovídat hodnota zadaná v [icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="fcd6d-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="fcd6d-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="fcd6d-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="fcd6d-108">Kanál úspěšně přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="fcd6d-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="fcd6d-109">Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.</span><span class="sxs-lookup"><span data-stu-id="fcd6d-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="fcd6d-110">To umožňuje snadno párování Vzdálená volání a vytvoření zásobníku logické volání.</span><span class="sxs-lookup"><span data-stu-id="fcd6d-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="fcd6d-111">[v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="fcd6d-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcd6d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcd6d-112">Requirements</span></span>  
 <span data-ttu-id="fcd6d-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcd6d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcd6d-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fcd6d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcd6d-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcd6d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcd6d-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcd6d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd6d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcd6d-117">See Also</span></span>  
 [<span data-ttu-id="fcd6d-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcd6d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
