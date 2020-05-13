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
ms.openlocfilehash: 39b4e7e5123447a36254b55b6168c80e48c8dcab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205452"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="34ae8-102">ICorDebugFrame::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="34ae8-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="34ae8-103">Získá stepper, který umožňuje ladicímu programu provádět operace krokování vzhledem k tomuto ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="34ae8-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34ae8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34ae8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34ae8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34ae8-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="34ae8-106">mimo Ukazatel na adresu objektu ICorDebugStepper, který umožňuje ladicímu programu provádět operace krokování vzhledem k aktuálnímu snímku.</span><span class="sxs-lookup"><span data-stu-id="34ae8-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34ae8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34ae8-107">Remarks</span></span>  
 <span data-ttu-id="34ae8-108">Pokud není rámec aktivní, objekt stepper se obvykle musí vrátit do rámce před dokončením kroku.</span><span class="sxs-lookup"><span data-stu-id="34ae8-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34ae8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34ae8-109">Requirements</span></span>  
 <span data-ttu-id="34ae8-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34ae8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34ae8-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34ae8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34ae8-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34ae8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34ae8-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34ae8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
