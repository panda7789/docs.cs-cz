---
title: "ICorProfilerCallback::RemotingClientReceivingReply – metoda"
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
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 831ce047f38f7f4a5c7a8b84efea423c482a418d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="f34be-102">ICorProfilerCallback::RemotingClientReceivingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="f34be-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="f34be-103">Upozorní profileru, který na straně serveru část vzdáleného volání bylo dokončeno a klient nyní získává a rozhodli jste se zpracovat odpověď.</span><span class="sxs-lookup"><span data-stu-id="f34be-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f34be-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="f34be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f34be-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="f34be-106">[v] Hodnota, která bude odpovídat s hodnota zadaná v [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="f34be-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="f34be-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="f34be-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="f34be-108">Kanál úspěšně přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="f34be-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="f34be-109">Identifikátor GUID soubory cookie jsou aktivní na straně serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="f34be-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="f34be-110">To umožňuje snadno párování Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="f34be-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f34be-111">[v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="f34be-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f34be-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f34be-112">Requirements</span></span>  
 <span data-ttu-id="f34be-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f34be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f34be-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f34be-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f34be-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f34be-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f34be-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f34be-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34be-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f34be-117">See Also</span></span>  
 [<span data-ttu-id="f34be-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f34be-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
