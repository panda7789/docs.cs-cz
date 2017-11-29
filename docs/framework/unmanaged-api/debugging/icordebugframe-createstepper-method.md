---
title: "ICorDebugFrame::CreateStepper – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6f575febc488d01700c32198d4c00916dd5e249
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="da937-102">ICorDebugFrame::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="da937-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="da937-103">Získá krokovač, které umožňuje provádět operace taktování relativně k této ICorDebugFrame ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="da937-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da937-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da937-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da937-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da937-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="da937-106">[out] Ukazatel na adresu ICorDebugStepper objekt, který umožňuje ladicí program k provádění operací taktování vzhledem k aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="da937-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da937-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da937-107">Remarks</span></span>  
 <span data-ttu-id="da937-108">Pokud rámečku není aktivní, objekt krokovač obvykle mají se vraťte do rámečku před dokončením kroku.</span><span class="sxs-lookup"><span data-stu-id="da937-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da937-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da937-109">Requirements</span></span>  
 <span data-ttu-id="da937-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da937-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da937-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da937-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da937-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da937-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da937-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da937-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
