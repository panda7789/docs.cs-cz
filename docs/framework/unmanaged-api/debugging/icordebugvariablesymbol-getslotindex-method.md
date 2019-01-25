---
title: ICorDebugVariableSymbol::GetSlotIndex – metoda
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09b50af49f8379539773d2000a6c1f8222fee875
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563831"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="4cc3d-102">ICorDebugVariableSymbol::GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="4cc3d-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="4cc3d-103">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="4cc3d-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cc3d-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cc3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cc3d-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="4cc3d-106">[out] Ukazatel na lokální proměnná pozici indexu.</span><span class="sxs-lookup"><span data-stu-id="4cc3d-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cc3d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4cc3d-107">Return Value</span></span>  
 <span data-ttu-id="4cc3d-108">`S_OK` v případě úspěšného ověření.</span><span class="sxs-lookup"><span data-stu-id="4cc3d-108">`S_OK` if successful.</span></span> <span data-ttu-id="4cc3d-109">`E_FAIL` Pokud je proměnná argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="4cc3d-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cc3d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cc3d-110">Remarks</span></span>  
 <span data-ttu-id="4cc3d-111">Spravované slotu index lokální proměnná slouží k načtení informací o metadatech proměnné</span><span class="sxs-lookup"><span data-stu-id="4cc3d-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cc3d-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4cc3d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cc3d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cc3d-113">Requirements</span></span>  
 <span data-ttu-id="4cc3d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cc3d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc3d-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cc3d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cc3d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cc3d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cc3d-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc3d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc3d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cc3d-118">See also</span></span>
- [<span data-ttu-id="4cc3d-119">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cc3d-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="4cc3d-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4cc3d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
