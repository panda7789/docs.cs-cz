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
ms.openlocfilehash: c60af0ccfb143e68be3b987b0caf92fe3d992b4d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212705"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="50aa8-102">ICorDebugManagedCallback::LogMessage – metoda</span><span class="sxs-lookup"><span data-stu-id="50aa8-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="50aa8-103">Oznamuje ladicímu programu, že spravované vlákno modulu CLR (Common Language Runtime) zavolalo do <xref:System.Diagnostics.EventLog> protokolu události metodu ve třídě.</span><span class="sxs-lookup"><span data-stu-id="50aa8-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50aa8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50aa8-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50aa8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50aa8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="50aa8-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno, které událost zaznamenal.</span><span class="sxs-lookup"><span data-stu-id="50aa8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="50aa8-107">pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="50aa8-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="50aa8-108">pro Hodnota výčtu [LoggingLevelEnum –](logginglevelenum-enumeration.md) , která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="50aa8-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="50aa8-109">pro Ukazatel na název sledovacího přepínače.</span><span class="sxs-lookup"><span data-stu-id="50aa8-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="50aa8-110">pro Ukazatel na zprávu, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="50aa8-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50aa8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50aa8-111">Requirements</span></span>  
 <span data-ttu-id="50aa8-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50aa8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50aa8-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50aa8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50aa8-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="50aa8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50aa8-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50aa8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50aa8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="50aa8-116">See also</span></span>

- [<span data-ttu-id="50aa8-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50aa8-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
