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
ms.openlocfilehash: 9d7432771a7d8eee9cea10f883dd3bd91f5ffb74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761386"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="8522c-102">ICorDebugManagedCallback::LogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="8522c-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="8522c-103">Ladicí program upozorní, že společným pojítkem language runtime (CLR) spravované volal metodu <xref:System.Diagnostics.Switch> třídy k vytvoření, úpravě nebo odstranění přepínače ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="8522c-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8522c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8522c-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8522c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8522c-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="8522c-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákna, které vytvořili, změněn nebo odstraněn přepínač ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="8522c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8522c-107">[in] Ukazatel na objekt ICorDebugThread, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="8522c-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="8522c-108">[in] Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="8522c-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="8522c-109">[in] Hodnota [logswitchcallreason –](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) výčet, který označuje, operace provedené na přepínač ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="8522c-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="8522c-110">[in] Ukazatel na název přepínače, ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="8522c-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="8522c-111">[in] Ukazatel na název nadřazeného přepínače, ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="8522c-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8522c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8522c-112">Requirements</span></span>  
 <span data-ttu-id="8522c-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8522c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8522c-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8522c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8522c-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8522c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8522c-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8522c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8522c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8522c-117">See also</span></span>

- [<span data-ttu-id="8522c-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8522c-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
