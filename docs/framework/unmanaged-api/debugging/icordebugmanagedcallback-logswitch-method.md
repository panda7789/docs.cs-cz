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
ms.openlocfilehash: 46c8b3fb2c9e7c353f74ef589e21f2a61df618fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777319"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="84160-102">ICorDebugManagedCallback::LogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="84160-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="84160-103">Oznamuje ladicímu programu, že spravované vlákno modulu CLR (Common Language Runtime) volalo metodu ve třídě <xref:System.Diagnostics.Switch> k vytvoření, úpravě nebo odstranění přepínače ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="84160-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84160-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84160-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84160-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84160-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="84160-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno, které vytvořil, upravil nebo odstranil přepínač ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="84160-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="84160-107">pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="84160-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="84160-108">pro Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="84160-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="84160-109">pro Hodnota výčtu [LogSwitchCallReason –](logswitchcallreason-enumeration.md) , která označuje operaci prováděnou na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="84160-109">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="84160-110">pro Ukazatel na název přepínače ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="84160-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="84160-111">pro Ukazatel na název nadřazeného přepínače ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="84160-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84160-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84160-112">Requirements</span></span>  
 <span data-ttu-id="84160-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84160-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84160-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84160-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84160-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="84160-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84160-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84160-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84160-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84160-117">See also</span></span>

- [<span data-ttu-id="84160-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84160-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
