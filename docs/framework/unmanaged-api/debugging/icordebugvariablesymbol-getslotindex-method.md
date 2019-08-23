---
title: 'ICorDebugVariableSymbol:: GetSlotIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58bb2cc63f2336ca9cfbed8ebeac0d607c18b2c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968160"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="505db-102">ICorDebugVariableSymbol:: GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="505db-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="505db-103">Načte index spravovaného slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="505db-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="505db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="505db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="505db-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="505db-106">mimo Ukazatel na index slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="505db-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="505db-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="505db-107">Return Value</span></span>  
 <span data-ttu-id="505db-108">`S_OK`v případě úspěchu.</span><span class="sxs-lookup"><span data-stu-id="505db-108">`S_OK` if successful.</span></span> <span data-ttu-id="505db-109">`E_FAIL`je-li proměnná argumentem funkce.</span><span class="sxs-lookup"><span data-stu-id="505db-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="505db-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="505db-110">Remarks</span></span>  
 <span data-ttu-id="505db-111">K načtení informací o metadatech proměnné lze použít index spravované patice místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="505db-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="505db-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="505db-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="505db-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="505db-113">Requirements</span></span>  
 <span data-ttu-id="505db-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="505db-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="505db-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="505db-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="505db-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="505db-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="505db-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="505db-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505db-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="505db-118">See also</span></span>

- [<span data-ttu-id="505db-119">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="505db-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="505db-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="505db-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
