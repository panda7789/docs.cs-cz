---
title: ICorProfilerCallback::RemotingServerReceivingMessage – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 157e6bc6cb9603fa9558ad6d39f0b086849fc7b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499893"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="65474-102">ICorProfilerCallback::RemotingServerReceivingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="65474-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="65474-103">Upozorní profileru, že proces přijal volání vzdálené metody nebo žádost o aktivaci.</span><span class="sxs-lookup"><span data-stu-id="65474-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65474-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65474-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65474-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65474-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="65474-106">pro Hodnota, která bude odpovídat hodnotě zadané v [ICorProfilerCallback:: remotingclientsendingmessage –](icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="65474-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="65474-107">Soubory cookie vzdálené komunikace jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="65474-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="65474-108">Kanál se úspěšně přenáší do zprávy.</span><span class="sxs-lookup"><span data-stu-id="65474-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="65474-109">Soubory cookie identifikátorů GUID jsou aktivní v procesu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="65474-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="65474-110">To umožňuje snadné párování volání vzdálené komunikace a vytváření logických zásobníků volání.</span><span class="sxs-lookup"><span data-stu-id="65474-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="65474-111">pro Hodnota, která je v `true` případě, že volání je asynchronní, v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="65474-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65474-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65474-112">Remarks</span></span>  
 <span data-ttu-id="65474-113">Pokud je žádost o zprávu asynchronní, může být žádost obsluhovaná libovolným vláknem.</span><span class="sxs-lookup"><span data-stu-id="65474-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65474-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65474-114">Requirements</span></span>  
 <span data-ttu-id="65474-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65474-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65474-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="65474-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65474-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65474-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65474-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65474-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65474-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65474-119">See also</span></span>

- [<span data-ttu-id="65474-120">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65474-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
