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
ms.openlocfilehash: 7fadffaab6eee5beed513f339ea300acef5a1c6b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378993"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="f6b60-102">ICorDebugStepper::SetRangeIL – metoda</span><span class="sxs-lookup"><span data-stu-id="f6b60-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="f6b60-103">Nastaví hodnotu, která určuje, zda volání [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) předávají hodnoty argumentů, které jsou relativní vzhledem k nativnímu kódu nebo relativně k kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="f6b60-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6b60-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6b60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6b60-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="f6b60-106">pro Nastavte na hodnotu `true` , chcete-li určit, že rozsahy jsou relativní vzhledem k kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="f6b60-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="f6b60-107">Nastavte na hodnotu `false` , chcete-li určit, že rozsahy jsou relativní vzhledem k nativnímu kódu.</span><span class="sxs-lookup"><span data-stu-id="f6b60-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="f6b60-108">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f6b60-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b60-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6b60-109">Requirements</span></span>  
 <span data-ttu-id="f6b60-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6b60-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6b60-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f6b60-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6b60-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f6b60-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6b60-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6b60-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
