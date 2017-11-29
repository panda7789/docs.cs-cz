---
title: "ICorDebugThread::CreateStepper – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b66c3e536104a46b65c92fe038fb5a92d79db299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="0a027-102">ICorDebugThread::CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="0a027-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="0a027-103">Vytvoří objekt ICorDebugStepper, který umožňuje procházení aktivní rámec této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="0a027-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a027-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a027-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a027-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a027-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="0a027-106">[out] Ukazatel na adresu `ICorDebugStepper` objekt, který umožňuje procházení aktivní rámec tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="0a027-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a027-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a027-107">Remarks</span></span>  
 <span data-ttu-id="0a027-108">Nespravovaný kód může být aktivní rámec.</span><span class="sxs-lookup"><span data-stu-id="0a027-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="0a027-109">`ICorDebugStepper` Rozhraní musí lze použít k provedení skutečné krokování.</span><span class="sxs-lookup"><span data-stu-id="0a027-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a027-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a027-110">Requirements</span></span>  
 <span data-ttu-id="0a027-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a027-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a027-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a027-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a027-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a027-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a027-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a027-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
