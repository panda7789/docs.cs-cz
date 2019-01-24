---
title: ICorDebugManagedCallback::LogMessage – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61a8d3e4a343818918e140727d3770ba3e82aac8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574687"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="adc58-102">ICorDebugManagedCallback::LogMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="adc58-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="adc58-103">Ladicí program upozorní, že společným pojítkem language runtime (CLR) spravované volal metodu <xref:System.Diagnostics.EventLog> třídy do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="adc58-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adc58-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="adc58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="adc58-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="adc58-106">[in] Ukazatel na objekt, který představuje doménu aplikace obsahující spravovaná vlákna, která událost zaznamenala ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="adc58-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="adc58-107">[in] Ukazatel na objekt ICorDebugThread, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="adc58-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="adc58-108">[in] Hodnota [logginglevelenum –](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) výčet, který indikuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="adc58-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="adc58-109">[in] Ukazatel na název přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="adc58-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="adc58-110">[in] Ukazatel na zprávu, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="adc58-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc58-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="adc58-111">Requirements</span></span>  
 <span data-ttu-id="adc58-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc58-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc58-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adc58-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adc58-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adc58-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adc58-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc58-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc58-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adc58-116">See also</span></span>
- [<span data-ttu-id="adc58-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="adc58-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
