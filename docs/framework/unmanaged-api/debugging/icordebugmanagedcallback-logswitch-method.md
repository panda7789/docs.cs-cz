---
title: "ICorDebugManagedCallback::LogSwitch – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: beb4dc25d634f64d8740005abf83e51ec1e3e731
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="9533d-102">ICorDebugManagedCallback::LogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="9533d-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="9533d-103">Ladicí program upozorní, že běžné vlákna modulu runtime (CLR) spravované jazyk volal metodu <xref:System.Diagnostics.Switch> třída k vytvoření, úpravě nebo odstranění přepínač ladění nebo trasování.</span><span class="sxs-lookup"><span data-stu-id="9533d-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9533d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9533d-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9533d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9533d-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="9533d-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující spravované vlákno, které vytvořit, upravit nebo odstranit přepínač ladění nebo trasování.</span><span class="sxs-lookup"><span data-stu-id="9533d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9533d-107">[v] Ukazatel ICorDebugThread objektu, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="9533d-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="9533d-108">[v] Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="9533d-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="9533d-109">[v] Hodnota [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) výčtu, která určuje operaci provést na přepínači ladění nebo trasování.</span><span class="sxs-lookup"><span data-stu-id="9533d-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="9533d-110">[v] Ukazatel na název přepínače ladění nebo trasování.</span><span class="sxs-lookup"><span data-stu-id="9533d-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="9533d-111">[v] Ukazatel na název nadřazené přepínače ladění nebo trasování.</span><span class="sxs-lookup"><span data-stu-id="9533d-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9533d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9533d-112">Requirements</span></span>  
 <span data-ttu-id="9533d-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9533d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9533d-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9533d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9533d-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9533d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9533d-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9533d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9533d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9533d-117">See Also</span></span>  
 [<span data-ttu-id="9533d-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9533d-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
