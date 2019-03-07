---
title: ICorProfilerCallback::RemotingClientReceivingReply – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5b25706353d999ab6875092e31f554438f28c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469154"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="fd173-102">ICorProfilerCallback::RemotingClientReceivingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="fd173-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="fd173-103">Oznámí profileru, který je dokončená část vzdálené volání na straně serveru a nyní přijímá klienta a o zpracování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="fd173-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd173-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd173-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fd173-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd173-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="fd173-106">[in] Hodnotu, která bude odpovídat s hodnotou v [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="fd173-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="fd173-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="fd173-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="fd173-108">Kanál úspěšně odesílá zprávu.</span><span class="sxs-lookup"><span data-stu-id="fd173-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="fd173-109">Identifikátor GUID soubory cookie jsou aktivní na straně serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="fd173-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="fd173-110">To umožňuje snadno párování Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="fd173-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="fd173-111">[in] Hodnotu, která je `true` Pokud je volání asynchronní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="fd173-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd173-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd173-112">Requirements</span></span>  
 <span data-ttu-id="fd173-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd173-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd173-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd173-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd173-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd173-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd173-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd173-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd173-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd173-117">See also</span></span>
- [<span data-ttu-id="fd173-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd173-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
