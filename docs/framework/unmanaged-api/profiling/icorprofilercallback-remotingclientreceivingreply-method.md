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
ms.openlocfilehash: 5865935af96260982d47b778d208f4235f6245e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775021"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="4a4e2-102">ICorProfilerCallback::RemotingClientReceivingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="4a4e2-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="4a4e2-103">Oznámí profileru, který je dokončená část vzdálené volání na straně serveru a nyní přijímá klienta a o zpracování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a4e2-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="4a4e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a4e2-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="4a4e2-106">[in] Hodnotu, která bude odpovídat s hodnotou v [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="4a4e2-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="4a4e2-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="4a4e2-108">Kanál úspěšně odesílá zprávu.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="4a4e2-109">Identifikátor GUID soubory cookie jsou aktivní na straně serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="4a4e2-110">To umožňuje snadno párování Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="4a4e2-111">[in] Hodnotu, která je `true` Pokud je volání asynchronní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a4e2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a4e2-112">Requirements</span></span>  
 <span data-ttu-id="4a4e2-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a4e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a4e2-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a4e2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a4e2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a4e2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a4e2-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a4e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a4e2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a4e2-117">See also</span></span>

- [<span data-ttu-id="4a4e2-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a4e2-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
