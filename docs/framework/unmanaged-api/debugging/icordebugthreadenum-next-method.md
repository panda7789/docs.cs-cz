---
title: ICorDebugThreadEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b80e0cc026ce80950c14436abb2e84548f9adb64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903315"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="bb563-102">ICorDebugThreadEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="bb563-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="bb563-103">Získá počet instancí zadané ICorDebugThread z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="bb563-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb563-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb563-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb563-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb563-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bb563-106">[in] Počet `ICorDebugThread` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="bb563-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="bb563-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugThread` objekt, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="bb563-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bb563-108">[out] Ukazatel na počet `ICorDebugThread` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="bb563-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="bb563-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="bb563-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb563-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb563-110">Requirements</span></span>  
 <span data-ttu-id="bb563-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb563-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb563-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb563-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb563-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb563-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb563-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb563-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
