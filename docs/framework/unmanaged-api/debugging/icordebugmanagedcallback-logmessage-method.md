---
title: "ICorDebugManagedCallback::LogMessage – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LogMessage
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f06e737498f2c12b041467f5f66de55c602615f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="56f6a-102">ICorDebugManagedCallback::LogMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="56f6a-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="56f6a-103">Ladicí program upozorní, že běžné vlákna modulu runtime (CLR) spravované jazyk volal metodu <xref:System.Diagnostics.EventLog> třída do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="56f6a-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f6a-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56f6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56f6a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="56f6a-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující spravovaných vláken, která událost zaznamenala.</span><span class="sxs-lookup"><span data-stu-id="56f6a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="56f6a-107">[v] Ukazatel ICorDebugThread objektu, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="56f6a-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="56f6a-108">[v] Hodnota [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) výčtu, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="56f6a-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="56f6a-109">[v] Ukazatel na název přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="56f6a-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="56f6a-110">[v] Ukazatel na zprávu, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="56f6a-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f6a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f6a-111">Requirements</span></span>  
 <span data-ttu-id="56f6a-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f6a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56f6a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56f6a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56f6a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f6a-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f6a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="56f6a-116">See Also</span></span>  
 [<span data-ttu-id="56f6a-117">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="56f6a-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
