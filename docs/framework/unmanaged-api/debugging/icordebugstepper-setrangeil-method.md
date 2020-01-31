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
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791755"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="72d2c-102">ICorDebugStepper::SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="72d2c-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="72d2c-103">Nastaví hodnotu, která určuje, zda volání [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) předávají hodnoty argumentů, které jsou relativní vzhledem k nativnímu kódu nebo relativně k kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="72d2c-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72d2c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72d2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72d2c-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="72d2c-106">pro Nastavte na `true` a určete tak, že rozsahy jsou relativní vzhledem k kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="72d2c-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="72d2c-107">Nastavte na `false` a určete tak, že rozsahy jsou relativní vzhledem k nativnímu kódu.</span><span class="sxs-lookup"><span data-stu-id="72d2c-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="72d2c-108">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="72d2c-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72d2c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72d2c-109">Requirements</span></span>  
 <span data-ttu-id="72d2c-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72d2c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d2c-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72d2c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72d2c-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="72d2c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72d2c-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72d2c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
