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
ms.openlocfilehash: 3fe3cbc4bad83496bcc58aaea60e6724b1d1f06c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466385"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="ad342-102">ICorDebugFrame::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="ad342-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="ad342-103">Získá krokovač, umožňující ladicího programu k provádění operací krokování vzhledem k této ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="ad342-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad342-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad342-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad342-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad342-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="ad342-106">[out] Ukazatel na adresu icordebugstepper – objekt, který umožňuje ladicího programu k provádění operací krokování vzhledem k aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="ad342-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad342-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad342-107">Remarks</span></span>  
 <span data-ttu-id="ad342-108">Pokud rámce není aktivní, obvykle muset objekt krokovač vrátit na snímek před dokončení tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="ad342-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad342-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad342-109">Requirements</span></span>  
 <span data-ttu-id="ad342-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad342-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad342-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad342-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad342-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad342-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad342-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad342-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
