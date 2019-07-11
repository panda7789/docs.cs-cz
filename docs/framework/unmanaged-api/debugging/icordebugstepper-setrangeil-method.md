---
title: ICorDebugStepper::SetRangeIL – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610225708bf990850fce73d6d7ff66c556e24e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760602"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="a1ef7-102">ICorDebugStepper::SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="a1ef7-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="a1ef7-103">Nastaví hodnotu, která určuje, zda volání [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předat argument hodnoty, které jsou relativní vzhledem k nativního kódu nebo relativní k Microsoft zprostředkující kód jazyka MSIL metody, která je právě zvyšována prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ef7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1ef7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ef7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1ef7-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="a1ef7-106">[in] Nastavte na `true` k určení, zda tyto rozsahy jsou relativní vzhledem k kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="a1ef7-107">Nastavte na `false` k určení, zda tyto rozsahy jsou relativní vzhledem k nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="a1ef7-108">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="a1ef7-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ef7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1ef7-109">Requirements</span></span>  
 <span data-ttu-id="a1ef7-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ef7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ef7-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1ef7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1ef7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ef7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1ef7-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ef7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
