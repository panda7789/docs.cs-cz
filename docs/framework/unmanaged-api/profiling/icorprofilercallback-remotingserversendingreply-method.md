---
title: ICorProfilerCallback::RemotingServerSendingReply – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cde75f1f33df83131212b0f7d4b349b20338f3dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662876"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="f8193-102">ICorProfilerCallback::RemotingServerSendingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="f8193-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="f8193-103">Profiler upozorní, že procesu bylo dokončeno zpracování požadavku volání vzdálené metody a je přenášet odpovědi prostřednictvím kanálu.</span><span class="sxs-lookup"><span data-stu-id="f8193-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8193-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8193-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8193-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8193-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="f8193-106">[in] Ukazatel na identifikátor GUID, který bude odpovídat hodnotu podle [icorprofilercallback::remotingclientreceivingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="f8193-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="f8193-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="f8193-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="f8193-108">Kanál úspěšně odesílá zprávu.</span><span class="sxs-lookup"><span data-stu-id="f8193-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="f8193-109">Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.</span><span class="sxs-lookup"><span data-stu-id="f8193-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="f8193-110">To umožňuje snadno párování tvorby logické volání zásobníku a Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="f8193-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f8193-111">[in] Hodnotu, která je `true` Pokud je volání asynchronní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f8193-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8193-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8193-112">Requirements</span></span>  
 <span data-ttu-id="f8193-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8193-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8193-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8193-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8193-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8193-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8193-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8193-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8193-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8193-117">See also</span></span>

- [<span data-ttu-id="f8193-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8193-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
