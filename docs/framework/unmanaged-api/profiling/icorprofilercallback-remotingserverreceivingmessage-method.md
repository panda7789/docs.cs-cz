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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67ec3bf10638538b49f1ec44ff583bdf4ba4ef9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572250"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="444ec-102">ICorProfilerCallback::RemotingServerReceivingMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="444ec-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="444ec-103">Oznámí profileru, že proces přijal žádost o vzdálené metody volání nebo aktivace.</span><span class="sxs-lookup"><span data-stu-id="444ec-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="444ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="444ec-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="444ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="444ec-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="444ec-106">[in] Hodnotu, která bude odpovídat s hodnotou v [icorprofilercallback::remotingclientsendingmessage –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="444ec-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="444ec-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="444ec-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="444ec-108">Kanál úspěšně odesílá zprávu.</span><span class="sxs-lookup"><span data-stu-id="444ec-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="444ec-109">Identifikátor GUID soubory cookie jsou aktivní na straně klienta procesu.</span><span class="sxs-lookup"><span data-stu-id="444ec-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="444ec-110">To umožňuje snadno párování tvorby logické volání zásobníku a Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="444ec-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="444ec-111">[in] Hodnotu, která je `true` Pokud je volání asynchronní; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="444ec-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="444ec-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="444ec-112">Remarks</span></span>  
 <span data-ttu-id="444ec-113">Pokud požadavek zprávy je asynchronní, žádost lze udržovat z žádného libovolného vlákna.</span><span class="sxs-lookup"><span data-stu-id="444ec-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="444ec-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="444ec-114">Requirements</span></span>  
 <span data-ttu-id="444ec-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="444ec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="444ec-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="444ec-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="444ec-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="444ec-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="444ec-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="444ec-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444ec-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="444ec-119">See also</span></span>
- [<span data-ttu-id="444ec-120">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="444ec-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
