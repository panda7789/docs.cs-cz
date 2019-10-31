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
ms.openlocfilehash: a72eabb1b405c67f5603164e56a589a237603d2f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130698"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="48262-102">ICorDebugManagedCallback::LogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="48262-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="48262-103">Oznamuje ladicímu programu, že spravované vlákno modulu CLR (Common Language Runtime) volalo metodu ve třídě <xref:System.Diagnostics.Switch> k vytvoření, úpravě nebo odstranění přepínače ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="48262-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48262-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48262-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48262-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48262-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="48262-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno, které vytvořil, upravil nebo odstranil přepínač ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="48262-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="48262-107">pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="48262-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="48262-108">pro Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="48262-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="48262-109">pro Hodnota výčtu [LogSwitchCallReason –](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) , která označuje operaci prováděnou na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="48262-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="48262-110">pro Ukazatel na název přepínače ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="48262-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="48262-111">pro Ukazatel na název nadřazeného přepínače ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="48262-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48262-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48262-112">Requirements</span></span>  
 <span data-ttu-id="48262-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48262-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48262-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="48262-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48262-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="48262-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48262-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48262-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48262-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48262-117">See also</span></span>

- [<span data-ttu-id="48262-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48262-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
