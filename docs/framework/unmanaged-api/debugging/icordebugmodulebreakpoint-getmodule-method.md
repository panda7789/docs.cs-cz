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
ms.openlocfilehash: 714819504099ea978ed31d471b4ceb9fc17a6552
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212292"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="fcd0d-102">ICorDebugModuleBreakpoint::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="fcd0d-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="fcd0d-103">Získá ukazatel rozhraní na "ICorDebugModule", který odkazuje na modul, ve kterém je tato zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="fcd0d-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcd0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcd0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcd0d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="fcd0d-106">mimo Ukazatel na adresu `ICorDebugModule` rozhraní, který odkazuje na modul, ve kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="fcd0d-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcd0d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcd0d-107">Requirements</span></span>  
 <span data-ttu-id="fcd0d-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcd0d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcd0d-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fcd0d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcd0d-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fcd0d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcd0d-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcd0d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd0d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcd0d-112">See also</span></span>
