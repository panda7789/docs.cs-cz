---
title: ICorDebugStepperEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58f148eb4c3206ba12eed41df670846d7beab77a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771633"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="473f9-102">ICorDebugStepperEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="473f9-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="473f9-103">Získá zadaný počet instancí icordebugstepper – z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="473f9-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="473f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="473f9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="473f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="473f9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="473f9-106">[in] Počet `ICorDebugStepper` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="473f9-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="473f9-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugStepper` objektu.</span><span class="sxs-lookup"><span data-stu-id="473f9-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="473f9-108">[out] Ukazatel na počet `ICorDebugStepper` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="473f9-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="473f9-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="473f9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473f9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="473f9-110">Requirements</span></span>  
 <span data-ttu-id="473f9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="473f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473f9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="473f9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="473f9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="473f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="473f9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
