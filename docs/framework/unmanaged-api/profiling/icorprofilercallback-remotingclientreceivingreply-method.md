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
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175132"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="8b544-102">ICorProfilerCallback::RemotingClientReceivingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="8b544-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="8b544-103">Upozorní profiler, že část vzdáleného volání na straně serveru byla dokončena a klient nyní přijímá a chystá se zpracovat odpověď.</span><span class="sxs-lookup"><span data-stu-id="8b544-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b544-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b544-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="8b544-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b544-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="8b544-106">[v] Hodnota, která bude odpovídat hodnotě uvedené v [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="8b544-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="8b544-107">Vzdálené soubory cookie GUID jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="8b544-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="8b544-108">Kanál úspěšně vysílá zprávu.</span><span class="sxs-lookup"><span data-stu-id="8b544-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="8b544-109">GuiD cookies jsou aktivní v procesu na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="8b544-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="8b544-110">To umožňuje snadné párování volání vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="8b544-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="8b544-111">[v] Hodnota, která `true` je, pokud je volání asynchronní; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="8b544-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b544-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b544-112">Requirements</span></span>  
 <span data-ttu-id="8b544-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b544-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b544-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b544-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b544-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b544-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b544-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b544-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b544-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b544-117">See also</span></span>

- [<span data-ttu-id="8b544-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b544-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
