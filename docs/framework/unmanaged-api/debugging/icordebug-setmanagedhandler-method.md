---
title: ICorDebug::SetManagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f30089879f2d023c8fb04b52e75b2942da2a83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786344"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="e4e87-102">ICorDebug::SetManagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="e4e87-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="e4e87-103">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="e4e87-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4e87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4e87-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4e87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4e87-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="e4e87-106">[in] Ukazatel [icordebugmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objekt, který je objekt obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e4e87-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4e87-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4e87-107">Remarks</span></span>  
 <span data-ttu-id="e4e87-108">`SetManagedHandler` musí být volána v okamžiku vytvoření.</span><span class="sxs-lookup"><span data-stu-id="e4e87-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="e4e87-109">Pokud `ICorDebugManagedCallback` implementace rozhraní dostatečné pro zpracování událostí ladění pro aplikace, která je právě laděna, neobsahuje `SetManagedHandler` vrací hodnotu HRESULT E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="e4e87-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4e87-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4e87-110">Requirements</span></span>  
 <span data-ttu-id="e4e87-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4e87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e87-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4e87-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4e87-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4e87-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4e87-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e87-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4e87-115">See also</span></span>

- [<span data-ttu-id="e4e87-116">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4e87-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
