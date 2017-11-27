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
ms.openlocfilehash: 5947541204edf7fd4359dfa3aca78ea62c8009c6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="f8ebe-102">ICorProfilerCallback::RemotingServerReceivingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="f8ebe-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="f8ebe-103">Upozorní profileru, že proces přijal žádost o vzdálené metody vyvolání nebo aktivace.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8ebe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8ebe-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8ebe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8ebe-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="f8ebe-106">[v] Hodnota, která bude odpovídat s hodnota zadaná v [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="f8ebe-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="f8ebe-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="f8ebe-108">Kanál úspěšně přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="f8ebe-109">Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="f8ebe-110">To umožňuje snadno párování Vzdálená volání a vytvoření zásobníku logické volání.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f8ebe-111">[v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8ebe-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8ebe-112">Remarks</span></span>  
 <span data-ttu-id="f8ebe-113">Pokud požadavek zprávy je asynchronní, žádost může obsluhovány pomocí libovolného libovolný vlákna.</span><span class="sxs-lookup"><span data-stu-id="f8ebe-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8ebe-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8ebe-114">Requirements</span></span>  
 <span data-ttu-id="f8ebe-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8ebe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8ebe-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8ebe-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8ebe-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8ebe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8ebe-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8ebe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ebe-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8ebe-119">See Also</span></span>  
 [<span data-ttu-id="f8ebe-120">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8ebe-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
