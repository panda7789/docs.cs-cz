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
ms.openlocfilehash: cb3c24b3a96a03359dc6983bcaac4a800613ff5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420528"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="28552-102">ICorDebugStepper::SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="28552-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="28552-103">Nastaví hodnotu, která určuje, zda volá, aby se [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předat hodnoty, které jsou relativní vzhledem k nativního kódu nebo relativně k Microsoft mezilehlé jazyk MSIL kód metody, která je právě stupeň argument prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="28552-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28552-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28552-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28552-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="28552-106">[v] Nastavte na `true` že rozsahy jsou relativní vzhledem k MSIL kód.</span><span class="sxs-lookup"><span data-stu-id="28552-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="28552-107">Nastavte na `false` že rozsahy jsou relativní vzhledem k nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="28552-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="28552-108">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="28552-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28552-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28552-109">Requirements</span></span>  
 <span data-ttu-id="28552-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28552-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28552-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28552-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28552-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28552-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28552-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28552-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
