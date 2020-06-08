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
ms.openlocfilehash: 820a37c8ca16f4962bf1d72b1f0f404cffd92a1a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499958"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="2ea37-102">ICorProfilerCallback::RemotingClientSendingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="2ea37-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="2ea37-103">Upozorní profileru, že klient posílá požadavek na server.</span><span class="sxs-lookup"><span data-stu-id="2ea37-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ea37-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ea37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ea37-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="2ea37-106">pro Hodnota, která odpovídá hodnotě zadané v [ICorProfilerCallback:: remotingserverreceivingmessage –](icorprofilercallback-remotingserverreceivingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="2ea37-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="2ea37-107">Soubory cookie vzdálené komunikace jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="2ea37-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="2ea37-108">Kanál se úspěšně přenáší do zprávy.</span><span class="sxs-lookup"><span data-stu-id="2ea37-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="2ea37-109">Soubory cookie GUID jsou v procesu na straně serveru aktivní.</span><span class="sxs-lookup"><span data-stu-id="2ea37-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="2ea37-110">To umožňuje snadné párování volání vzdálené komunikace a vytváření logických zásobníků volání.</span><span class="sxs-lookup"><span data-stu-id="2ea37-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="2ea37-111">pro Hodnota, která je v `true` případě, že volání je asynchronní, v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="2ea37-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea37-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ea37-112">Requirements</span></span>  
 <span data-ttu-id="2ea37-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea37-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea37-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2ea37-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ea37-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2ea37-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ea37-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea37-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea37-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ea37-117">See also</span></span>

- [<span data-ttu-id="2ea37-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ea37-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
