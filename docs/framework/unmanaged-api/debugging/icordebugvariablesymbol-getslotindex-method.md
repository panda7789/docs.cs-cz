---
title: 'ICorDebugVariableSymbol:: GetSlotIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: a7a7ecf7d3e3d0d2125b03d3604c44138a2be0cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120975"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="38353-102">ICorDebugVariableSymbol:: GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="38353-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="38353-103">Načte index spravovaného slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="38353-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38353-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38353-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38353-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38353-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="38353-106">mimo Ukazatel na index slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="38353-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38353-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38353-107">Return Value</span></span>  
 <span data-ttu-id="38353-108">`S_OK`, pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="38353-108">`S_OK` if successful.</span></span> <span data-ttu-id="38353-109">`E_FAIL`, je-li proměnná argumentem funkce.</span><span class="sxs-lookup"><span data-stu-id="38353-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38353-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38353-110">Remarks</span></span>  
 <span data-ttu-id="38353-111">K načtení informací o metadatech proměnné lze použít index spravované patice místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="38353-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38353-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38353-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38353-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38353-113">Requirements</span></span>  
 <span data-ttu-id="38353-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38353-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38353-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38353-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38353-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38353-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38353-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38353-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38353-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38353-118">See also</span></span>

- [<span data-ttu-id="38353-119">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38353-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="38353-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="38353-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
