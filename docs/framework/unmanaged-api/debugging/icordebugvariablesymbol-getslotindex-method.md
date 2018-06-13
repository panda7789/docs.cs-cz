---
title: ICorDebugVariableSymbol::GetSlotIndex – metoda
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420619"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="7514f-102">ICorDebugVariableSymbol::GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="7514f-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="7514f-103">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="7514f-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7514f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7514f-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7514f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7514f-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="7514f-106">[out] Ukazatel na místní proměnné pozici indexu.</span><span class="sxs-lookup"><span data-stu-id="7514f-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7514f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7514f-107">Return Value</span></span>  
 <span data-ttu-id="7514f-108">`S_OK` Pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="7514f-108">`S_OK` if successful.</span></span> <span data-ttu-id="7514f-109">`E_FAIL` Pokud je proměnná argument funkce.</span><span class="sxs-lookup"><span data-stu-id="7514f-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7514f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7514f-110">Remarks</span></span>  
 <span data-ttu-id="7514f-111">Index spravované slotu místní proměnné lze načíst informace o metadatech proměnné</span><span class="sxs-lookup"><span data-stu-id="7514f-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7514f-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="7514f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7514f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7514f-113">Requirements</span></span>  
 <span data-ttu-id="7514f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7514f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7514f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7514f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7514f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7514f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7514f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7514f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7514f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7514f-118">See Also</span></span>  
 [<span data-ttu-id="7514f-119">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7514f-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="7514f-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7514f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
