---
title: ICorProfilerCallback::RemotingClientSendingMessage – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14717b67db03b941d33b5df61c64b5df078adaa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451425"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="a6483-102">ICorProfilerCallback::RemotingClientSendingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="a6483-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="a6483-103">Upozorní profileru, že klient odesílá požadavek na server.</span><span class="sxs-lookup"><span data-stu-id="a6483-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6483-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6483-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6483-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6483-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="a6483-106">[v] Hodnota, která odpovídá s hodnota zadaná v [icorprofilercallback::remotingserverreceivingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="a6483-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="a6483-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="a6483-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="a6483-108">Kanál úspěšně přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="a6483-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="a6483-109">Identifikátor GUID soubory cookie jsou aktivní na straně serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="a6483-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="a6483-110">To umožňuje snadno párování Vzdálená volání a vytvoření zásobníku logické volání.</span><span class="sxs-lookup"><span data-stu-id="a6483-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="a6483-111">[v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="a6483-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6483-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6483-112">Requirements</span></span>  
 <span data-ttu-id="a6483-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6483-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6483-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6483-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6483-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6483-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6483-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6483-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6483-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6483-117">See Also</span></span>  
 [<span data-ttu-id="a6483-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6483-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
