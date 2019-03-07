---
title: ICorDebugManagedCallback::LogSwitch – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 040c7dea7f751accb801f8fda190e9387c7aede1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466164"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="d80d2-102">ICorDebugManagedCallback::LogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="d80d2-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="d80d2-103">Ladicí program upozorní, že společným pojítkem language runtime (CLR) spravované volal metodu <xref:System.Diagnostics.Switch> třídy k vytvoření, úpravě nebo odstranění přepínače ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="d80d2-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d80d2-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d80d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d80d2-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="d80d2-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákna, které vytvořili, změněn nebo odstraněn přepínač ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="d80d2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d80d2-107">[in] Ukazatel na objekt ICorDebugThread, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="d80d2-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d80d2-108">[in] Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="d80d2-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="d80d2-109">[in] Hodnota [logswitchcallreason –](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) výčet, který označuje, operace provedené na přepínač ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="d80d2-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="d80d2-110">[in] Ukazatel na název přepínače, ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="d80d2-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="d80d2-111">[in] Ukazatel na název nadřazeného přepínače, ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="d80d2-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d80d2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d80d2-112">Requirements</span></span>  
 <span data-ttu-id="d80d2-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d80d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d80d2-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d80d2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d80d2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d80d2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d80d2-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d80d2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80d2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d80d2-117">See also</span></span>
- [<span data-ttu-id="d80d2-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d80d2-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
