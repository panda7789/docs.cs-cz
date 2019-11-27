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
ms.openlocfilehash: e25cbfabc10da0c7b1095a956583bb5c7450dba9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445804"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="4a408-102">ICorProfilerCallback::RemotingClientReceivingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="4a408-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="4a408-103">Upozorní profileru, že je dokončena serverová část volání vzdálené komunikace a klient nyní přijímá a chystá zpracovat odpověď.</span><span class="sxs-lookup"><span data-stu-id="4a408-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a408-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a408-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="4a408-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a408-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="4a408-106">pro Hodnota, která bude odpovídat hodnotě zadané v [ICorProfilerCallback:: remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="4a408-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="4a408-107">Soubory cookie vzdálené komunikace jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="4a408-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="4a408-108">Kanál se úspěšně přenáší do zprávy.</span><span class="sxs-lookup"><span data-stu-id="4a408-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="4a408-109">Soubory cookie GUID jsou v procesu na straně serveru aktivní.</span><span class="sxs-lookup"><span data-stu-id="4a408-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="4a408-110">To umožňuje snadné párování volání vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="4a408-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="4a408-111">pro Hodnota, která je `true`, pokud je volání asynchronní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="4a408-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a408-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a408-112">Requirements</span></span>  
 <span data-ttu-id="4a408-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a408-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a408-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4a408-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a408-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4a408-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a408-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a408-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a408-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a408-117">See also</span></span>

- [<span data-ttu-id="4a408-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a408-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
