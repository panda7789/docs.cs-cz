---
title: ICorDebugModuleBreakpoint::GetModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cbb1aa9c81101eb818a9e7829c777efd3923b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416150"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="f9ccd-102">ICorDebugModuleBreakpoint::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="f9ccd-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="f9ccd-103">Získá ukazatele rozhraní umožňuje "ICorDebugModule" odkazující na modul, ve kterém je nastavený tento bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="f9ccd-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ccd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9ccd-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9ccd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9ccd-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="f9ccd-106">[out] Ukazatel na adresu `ICorDebugModule` rozhraní, které odkazuje na modul, ve kterém je nastaven breakpoint.</span><span class="sxs-lookup"><span data-stu-id="f9ccd-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ccd-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9ccd-107">Requirements</span></span>  
 <span data-ttu-id="f9ccd-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9ccd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ccd-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9ccd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9ccd-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9ccd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9ccd-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ccd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ccd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9ccd-112">See Also</span></span>  
 
