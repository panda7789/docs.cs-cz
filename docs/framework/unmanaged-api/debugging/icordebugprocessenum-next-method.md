---
title: ICorDebugProcessEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59efdb76c000a78007ec0321202793ed0dd50cfb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768285"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="425a7-102">ICorDebugProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="425a7-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="425a7-103">Získá zadaný počet instancí ICorDebugProcess z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="425a7-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="425a7-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="425a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="425a7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="425a7-106">[in] Počet `ICorDebugProcess` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="425a7-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="425a7-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugProcess` objekt, který reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="425a7-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="425a7-108">[out] Ukazatel na počet `ICorDebugProcess` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="425a7-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="425a7-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="425a7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425a7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="425a7-110">Requirements</span></span>  
 <span data-ttu-id="425a7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="425a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="425a7-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="425a7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="425a7-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="425a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="425a7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="425a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
