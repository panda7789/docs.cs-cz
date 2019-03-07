---
title: ICorDebugThread::CreateStepper – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89182739633984011aaab3d7900d376b6db5ef99
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476201"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="80efc-102">ICorDebugThread::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="80efc-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="80efc-103">Icordebugstepper – objekt, který umožňuje procházení aktivní rámec tohoto ICorDebugThread vytvoří.</span><span class="sxs-lookup"><span data-stu-id="80efc-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80efc-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80efc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80efc-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="80efc-106">[out] Ukazatel na adresu `ICorDebugStepper` objekt, který umožňuje procházení aktivní rámec tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="80efc-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80efc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80efc-107">Remarks</span></span>  
 <span data-ttu-id="80efc-108">Nespravovaný kód může být aktivní rámec.</span><span class="sxs-lookup"><span data-stu-id="80efc-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="80efc-109">`ICorDebugStepper` Rozhraní musíte použít k provedení skutečné krokování.</span><span class="sxs-lookup"><span data-stu-id="80efc-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80efc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80efc-110">Requirements</span></span>  
 <span data-ttu-id="80efc-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80efc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80efc-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80efc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80efc-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80efc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80efc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80efc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
