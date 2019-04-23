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
ms.openlocfilehash: 61a36ff23bf9deac25983f06387b2bbbfd49546b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133182"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="8a390-102">ICorProfilerCallback::RemotingClientSendingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="8a390-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="8a390-103">Oznámí profileru, že klient odesílá požadavek na server.</span><span class="sxs-lookup"><span data-stu-id="8a390-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a390-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a390-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a390-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a390-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="8a390-106">[in] Hodnota, která odpovídá s hodnotou v [icorprofilercallback::remotingserverreceivingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="8a390-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="8a390-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="8a390-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="8a390-108">Kanál úspěšně odesílá zprávu.</span><span class="sxs-lookup"><span data-stu-id="8a390-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="8a390-109">Identifikátor GUID soubory cookie jsou aktivní na straně serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="8a390-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="8a390-110">To umožňuje snadno párování tvorby logické volání zásobníku a Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="8a390-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="8a390-111">[in] Hodnotu, která je `true` Pokud je volání asynchronní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="8a390-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a390-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a390-112">Requirements</span></span>  
 <span data-ttu-id="8a390-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a390-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a390-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a390-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a390-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a390-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a390-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a390-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a390-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a390-117">See also</span></span>

- [<span data-ttu-id="8a390-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a390-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
