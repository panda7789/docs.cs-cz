---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda"
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
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 14258ef1ae473fc867d86c89ec877ddbf8c80213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="1edab-102">ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="1edab-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="1edab-103">Odebere dříve nastavené zarážku na danou adresu.</span><span class="sxs-lookup"><span data-stu-id="1edab-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1edab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1edab-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1edab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1edab-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1edab-106">[v] A `CORDB_ADDRESS` hodnotu, která určuje, kdy byl nastaven zarážce adresu.</span><span class="sxs-lookup"><span data-stu-id="1edab-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1edab-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1edab-107">Remarks</span></span>  
 <span data-ttu-id="1edab-108">Zadaný zarážek by byla dříve nastavena starší voláním [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="1edab-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="1edab-109">`ClearUnmanagedBreakpoint` Metodu lze volat, když proces laděné běží.</span><span class="sxs-lookup"><span data-stu-id="1edab-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="1edab-110">`ClearUnmanagedBreakpoint` Metoda vrací kód chyby, pokud je připojen ladicí program v režimu jen pro spravované nebo pokud neexistuje žádné zarážek na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="1edab-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1edab-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1edab-111">Requirements</span></span>  
 <span data-ttu-id="1edab-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1edab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1edab-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1edab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1edab-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1edab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1edab-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1edab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
