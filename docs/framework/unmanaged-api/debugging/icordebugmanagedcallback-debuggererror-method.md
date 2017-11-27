---
title: "ICorDebugManagedCallback::DebuggerError – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4eb16762d2a0db01c3cc921712a89995e0c87c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="f88f9-102">ICorDebugManagedCallback::DebuggerError – metoda</span><span class="sxs-lookup"><span data-stu-id="f88f9-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="f88f9-103">Upozorní ladicí program, že došlo k chybě při pokusu o zpracování události z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f88f9-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f88f9-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f88f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f88f9-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f88f9-106">[v] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve které došlo k události.</span><span class="sxs-lookup"><span data-stu-id="f88f9-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="f88f9-107">[v] Hodnota HRESULT, která byla vrácena z obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="f88f9-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="f88f9-108">[v] Celé číslo, které určuje chyba CLR.</span><span class="sxs-lookup"><span data-stu-id="f88f9-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f88f9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f88f9-109">Remarks</span></span>  
 <span data-ttu-id="f88f9-110">Proces může být zařazen do průchozí režimu, v závislosti na povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="f88f9-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="f88f9-111">`DebugError` Zpětného volání označuje, že ladění služby byly zakázány kvůli chybě, takže ladicí programy měli chybová zpráva k dispozici pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="f88f9-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="f88f9-112">[Icordebugprocess::getid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) bude bezpečné volání, ale všechny ostatní způsoby, včetně [icordebug::Terminate –](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměl být volán.</span><span class="sxs-lookup"><span data-stu-id="f88f9-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="f88f9-113">Ladicí program měli použít zařízení pro operační systém pro ukončení procesy.</span><span class="sxs-lookup"><span data-stu-id="f88f9-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f88f9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f88f9-114">Requirements</span></span>  
 <span data-ttu-id="f88f9-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f88f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f88f9-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f88f9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f88f9-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f88f9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f88f9-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f88f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f88f9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f88f9-119">See Also</span></span>  
 [<span data-ttu-id="f88f9-120">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="f88f9-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
