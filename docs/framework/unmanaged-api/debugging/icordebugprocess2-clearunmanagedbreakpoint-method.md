---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ca1514eaa916f5e607e49b5a5713763f855d937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="e005c-102">ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="e005c-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="e005c-103">Odebere dříve nastavené zarážku na danou adresu.</span><span class="sxs-lookup"><span data-stu-id="e005c-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e005c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e005c-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e005c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e005c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e005c-106">[v] A `CORDB_ADDRESS` hodnotu, která určuje, kdy byl nastaven zarážce adresu.</span><span class="sxs-lookup"><span data-stu-id="e005c-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e005c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e005c-107">Remarks</span></span>  
 <span data-ttu-id="e005c-108">Zadaný zarážek by byla dříve nastavena starší voláním [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="e005c-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="e005c-109">`ClearUnmanagedBreakpoint` Metodu lze volat, když proces laděné běží.</span><span class="sxs-lookup"><span data-stu-id="e005c-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="e005c-110">`ClearUnmanagedBreakpoint` Metoda vrací kód chyby, pokud je připojen ladicí program v režimu jen pro spravované nebo pokud neexistuje žádné zarážek na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="e005c-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e005c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e005c-111">Requirements</span></span>  
 <span data-ttu-id="e005c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e005c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e005c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e005c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e005c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e005c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e005c-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e005c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
