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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd105a5cbdb857aaa902e60968ff1d94473259b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754237"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="cd2fb-102">ICorDebugFrame::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="cd2fb-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="cd2fb-103">Získá krokovač, umožňující ladicího programu k provádění operací krokování vzhledem k této ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="cd2fb-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd2fb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd2fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd2fb-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="cd2fb-106">[out] Ukazatel na adresu icordebugstepper – objekt, který umožňuje ladicího programu k provádění operací krokování vzhledem k aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="cd2fb-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd2fb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd2fb-107">Remarks</span></span>  
 <span data-ttu-id="cd2fb-108">Pokud rámce není aktivní, obvykle muset objekt krokovač vrátit na snímek před dokončení tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="cd2fb-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2fb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd2fb-109">Requirements</span></span>  
 <span data-ttu-id="cd2fb-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd2fb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2fb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd2fb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd2fb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd2fb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd2fb-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2fb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
