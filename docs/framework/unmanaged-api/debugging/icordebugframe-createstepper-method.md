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
ms.openlocfilehash: 3662ed8a3fda5881b0e0929a830d19b0d805299f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411028"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="2e0fd-102">ICorDebugFrame::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="2e0fd-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="2e0fd-103">Získá krokovač, které umožňuje provádět operace taktování relativně k této ICorDebugFrame ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2e0fd-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e0fd-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e0fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e0fd-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="2e0fd-106">[out] Ukazatel na adresu ICorDebugStepper objekt, který umožňuje ladicí program k provádění operací taktování vzhledem k aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="2e0fd-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e0fd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e0fd-107">Remarks</span></span>  
 <span data-ttu-id="2e0fd-108">Pokud rámečku není aktivní, objekt krokovač obvykle mají se vraťte do rámečku před dokončením kroku.</span><span class="sxs-lookup"><span data-stu-id="2e0fd-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e0fd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e0fd-109">Requirements</span></span>  
 <span data-ttu-id="2e0fd-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e0fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e0fd-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e0fd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e0fd-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e0fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e0fd-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
