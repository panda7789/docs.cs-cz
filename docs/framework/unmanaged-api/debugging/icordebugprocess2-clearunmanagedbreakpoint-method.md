---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4dcfb977f5ca87f2219fd3ed8ef87d16c2defd2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472640"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="d85e7-102">ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="d85e7-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="d85e7-103">Odstraní dříve nastaveného zarážku na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="d85e7-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d85e7-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d85e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d85e7-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d85e7-106">[in] A `CORDB_ADDRESS` hodnotu, která určuje adresu, na který byla nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="d85e7-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d85e7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d85e7-107">Remarks</span></span>  
 <span data-ttu-id="d85e7-108">Zadaný zarážka by mohly být dříve nastaveny v dřívějším volání [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="d85e7-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="d85e7-109">`ClearUnmanagedBreakpoint` Metodu lze volat, pokud do něho laděný proces běží.</span><span class="sxs-lookup"><span data-stu-id="d85e7-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="d85e7-110">`ClearUnmanagedBreakpoint` Metoda vrací kód chyby, pokud je připojen ladicí program v režimu jen pro spravované nebo pokud neexistuje žádné zarážky na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="d85e7-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d85e7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d85e7-111">Requirements</span></span>  
 <span data-ttu-id="d85e7-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d85e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d85e7-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d85e7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d85e7-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d85e7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d85e7-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d85e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
