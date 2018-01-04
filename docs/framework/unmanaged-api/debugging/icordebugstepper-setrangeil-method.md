---
title: "ICorDebugStepper::SetRangeIL – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetRangeIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658f0164a73cfb5dbab0379eda2f61505865d2c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="80909-102">ICorDebugStepper::SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="80909-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="80909-103">Nastaví hodnotu, která určuje, zda volá, aby se [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předat hodnoty, které jsou relativní vzhledem k nativního kódu nebo relativně k Microsoft mezilehlé jazyk MSIL kód metody, která je právě stupeň argument prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="80909-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80909-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80909-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80909-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="80909-106">[v] Nastavte na `true` že rozsahy jsou relativní vzhledem k MSIL kód.</span><span class="sxs-lookup"><span data-stu-id="80909-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="80909-107">Nastavte na `false` že rozsahy jsou relativní vzhledem k nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="80909-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="80909-108">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="80909-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80909-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80909-109">Requirements</span></span>  
 <span data-ttu-id="80909-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80909-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80909-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80909-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80909-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80909-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80909-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80909-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
