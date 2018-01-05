---
title: "ICorProfilerCallback::RemotingServerReceivingMessage – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerReceivingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4542f5362d83bc5c0419b9f1ff389c9a21aad29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="eb906-102">ICorProfilerCallback::RemotingServerReceivingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="eb906-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="eb906-103">Upozorní profileru, že proces přijal žádost o vzdálené metody vyvolání nebo aktivace.</span><span class="sxs-lookup"><span data-stu-id="eb906-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb906-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb906-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb906-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb906-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="eb906-106">[v] Hodnota, která bude odpovídat s hodnota zadaná v [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="eb906-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="eb906-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="eb906-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="eb906-108">Kanál úspěšně přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="eb906-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="eb906-109">Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.</span><span class="sxs-lookup"><span data-stu-id="eb906-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="eb906-110">To umožňuje snadno párování Vzdálená volání a vytvoření zásobníku logické volání.</span><span class="sxs-lookup"><span data-stu-id="eb906-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="eb906-111">[v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="eb906-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb906-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb906-112">Remarks</span></span>  
 <span data-ttu-id="eb906-113">Pokud požadavek zprávy je asynchronní, žádost může obsluhovány pomocí libovolného libovolný vlákna.</span><span class="sxs-lookup"><span data-stu-id="eb906-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb906-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb906-114">Requirements</span></span>  
 <span data-ttu-id="eb906-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb906-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb906-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb906-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb906-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb906-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb906-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb906-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb906-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb906-119">See Also</span></span>  
 [<span data-ttu-id="eb906-120">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb906-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
