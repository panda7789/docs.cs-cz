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
ms.openlocfilehash: 293d1a9cd93b5ce45105427e7df864ad8bfbe77a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379196"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="8a128-102">ICorDebugStepperEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="8a128-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="8a128-103">Získá zadaný počet instancí ICorDebugStepper z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="8a128-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a128-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a128-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a128-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a128-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8a128-106">pro Počet instancí, `ICorDebugStepper` které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="8a128-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="8a128-107">mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugStepper` objekt.</span><span class="sxs-lookup"><span data-stu-id="8a128-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8a128-108">mimo Ukazatel na počet `ICorDebugStepper` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="8a128-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="8a128-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="8a128-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a128-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a128-110">Requirements</span></span>  
 <span data-ttu-id="8a128-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a128-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a128-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a128-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a128-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8a128-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a128-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a128-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
