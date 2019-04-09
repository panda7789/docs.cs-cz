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
ms.openlocfilehash: 51403c52d7f8a216e83b817f157979f4af1c433a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162865"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="0d0f3-102">ICorDebugModuleBreakpoint::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="0d0f3-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="0d0f3-103">Získá ukazatel rozhraní "ICorDebugModule", který odkazuje na modul, ve kterém je tato zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="0d0f3-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d0f3-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d0f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d0f3-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="0d0f3-106">[out] Ukazatel na adresu `ICorDebugModule` rozhraní, které odkazuje na modul, ve kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="0d0f3-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d0f3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d0f3-107">Requirements</span></span>  
 <span data-ttu-id="0d0f3-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d0f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d0f3-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d0f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d0f3-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d0f3-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0d0f3-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0d0f3-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d0f3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d0f3-112">See also</span></span>
