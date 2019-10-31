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
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137547"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="ecc97-102">ICorDebugStepper::SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="ecc97-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="ecc97-103">Nastaví hodnotu, která určuje, zda volání [ICorDebugStepper:: StepRange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předávají hodnoty argumentů, které jsou relativní vzhledem k nativnímu kódu nebo relativně k kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="ecc97-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc97-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecc97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecc97-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="ecc97-106">pro Nastavte na `true` a určete tak, že rozsahy jsou relativní vzhledem k kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="ecc97-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="ecc97-107">Nastavte na `false` a určete tak, že rozsahy jsou relativní vzhledem k nativnímu kódu.</span><span class="sxs-lookup"><span data-stu-id="ecc97-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="ecc97-108">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="ecc97-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc97-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecc97-109">Requirements</span></span>  
 <span data-ttu-id="ecc97-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc97-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc97-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ecc97-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecc97-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecc97-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecc97-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc97-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
