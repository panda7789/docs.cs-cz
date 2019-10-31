---
title: ICorDebugFrame::CreateStepper – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091034"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="b3702-102">ICorDebugFrame::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="b3702-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="b3702-103">Získá stepper, který umožňuje ladicímu programu provádět operace krokování vzhledem k tomuto ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="b3702-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3702-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3702-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3702-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3702-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="b3702-106">mimo Ukazatel na adresu objektu ICorDebugStepper, který umožňuje ladicímu programu provádět operace krokování vzhledem k aktuálnímu snímku.</span><span class="sxs-lookup"><span data-stu-id="b3702-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3702-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3702-107">Remarks</span></span>  
 <span data-ttu-id="b3702-108">Pokud není rámec aktivní, objekt stepper se obvykle musí vrátit do rámce před dokončením kroku.</span><span class="sxs-lookup"><span data-stu-id="b3702-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3702-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3702-109">Requirements</span></span>  
 <span data-ttu-id="b3702-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3702-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3702-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3702-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3702-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b3702-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3702-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3702-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
