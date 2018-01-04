---
title: "ICorDebug::SetManagedHandler – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetManagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dde32b6a8251474c4254e35a3a1ba3ba3bafcb8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="f9798-102">ICorDebug::SetManagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="f9798-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="f9798-103">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="f9798-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9798-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9798-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9798-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9798-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="f9798-106">[v] Ukazatel na [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objekt, který je objekt obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="f9798-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9798-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9798-107">Remarks</span></span>  
 <span data-ttu-id="f9798-108">`SetManagedHandler`musí být voláno v okamžiku vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f9798-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="f9798-109">Pokud `ICorDebugManagedCallback` implementace neobsahuje dostatek rozhraní pro zpracování události ladění pro aplikace, která je probíhá ladění, `SetManagedHandler` vrátí HRESULT E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="f9798-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9798-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9798-110">Requirements</span></span>  
 <span data-ttu-id="f9798-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9798-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9798-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9798-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9798-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9798-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9798-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9798-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9798-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9798-115">See Also</span></span>  
 [<span data-ttu-id="f9798-116">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9798-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
