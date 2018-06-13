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
ms.openlocfilehash: 04956fb5519c66141f4bd7330367f6c78b4e7bc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453955"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="6f936-102">ICorProfilerCallback::RemotingClientReceivingReply – metoda</span><span class="sxs-lookup"><span data-stu-id="6f936-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="6f936-103">Upozorní profileru, který na straně serveru část vzdáleného volání bylo dokončeno a klient nyní získává a rozhodli jste se zpracovat odpověď.</span><span class="sxs-lookup"><span data-stu-id="6f936-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f936-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f936-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f936-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f936-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="6f936-106">[v] Hodnota, která bude odpovídat s hodnota zadaná v [icorprofilercallback::remotingserversendingreply –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) za těchto podmínek:</span><span class="sxs-lookup"><span data-stu-id="6f936-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="6f936-107">Vzdálená komunikace GUID soubory cookie jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="6f936-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="6f936-108">Kanál úspěšně přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="6f936-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="6f936-109">Identifikátor GUID soubory cookie jsou aktivní na straně serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="6f936-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="6f936-110">To umožňuje snadno párování Vzdálená volání.</span><span class="sxs-lookup"><span data-stu-id="6f936-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="6f936-111">[v] Hodnotu, která je `true` Pokud volání je asynchronní, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="6f936-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f936-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f936-112">Requirements</span></span>  
 <span data-ttu-id="6f936-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f936-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f936-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f936-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f936-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f936-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f936-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f936-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f936-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f936-117">See Also</span></span>  
 [<span data-ttu-id="6f936-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f936-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
