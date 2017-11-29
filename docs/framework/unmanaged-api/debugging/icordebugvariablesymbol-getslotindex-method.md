---
title: "ICorDebugVariableSymbol::GetSlotIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d632bc792152afcfc94b51235dc0699fb3efc245
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="29abe-102">ICorDebugVariableSymbol::GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="29abe-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="29abe-103">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="29abe-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29abe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29abe-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29abe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29abe-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="29abe-106">[out] Ukazatel na místní proměnné pozici indexu.</span><span class="sxs-lookup"><span data-stu-id="29abe-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29abe-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29abe-107">Return Value</span></span>  
 <span data-ttu-id="29abe-108">`S_OK`Pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="29abe-108">`S_OK` if successful.</span></span> <span data-ttu-id="29abe-109">`E_FAIL`Pokud je proměnná argument funkce.</span><span class="sxs-lookup"><span data-stu-id="29abe-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29abe-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29abe-110">Remarks</span></span>  
 <span data-ttu-id="29abe-111">Index spravované slotu místní proměnné lze načíst informace o metadatech proměnné</span><span class="sxs-lookup"><span data-stu-id="29abe-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29abe-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="29abe-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29abe-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29abe-113">Requirements</span></span>  
 <span data-ttu-id="29abe-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29abe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29abe-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29abe-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29abe-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29abe-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29abe-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29abe-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29abe-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="29abe-118">See Also</span></span>  
 [<span data-ttu-id="29abe-119">ICorDebugVariableSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="29abe-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="29abe-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="29abe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
