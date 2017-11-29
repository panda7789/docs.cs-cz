---
title: "ICorDebugVariableSymbol::SetValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12c13259d20301b0f485a6041fa884b0996cbbdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="788d1-102">ICorDebugVariableSymbol::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="788d1-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="788d1-103">Proměnné přiřazuje hodnoty bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="788d1-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="788d1-104">Syntax</span></span>  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="788d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="788d1-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="788d1-106">[v] Počáteční odsazení v proměnné, pro kterou chcete nastavit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="788d1-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="788d1-107">Tento parametr je použit při zápisu do pole člena v objektu.</span><span class="sxs-lookup"><span data-stu-id="788d1-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="788d1-108">[v] Identifikátor vlákno vlákna, jehož kontext musí být aktualizovány tak, aby odrážely novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="788d1-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="788d1-109">[v] Velikost v bajtech kontextu přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="788d1-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="788d1-110">[v] Vlákno kontext, který používá pro zápis hodnoty.</span><span class="sxs-lookup"><span data-stu-id="788d1-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="788d1-111">[v] Velikost v bajtech `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="788d1-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="788d1-112">[v] Vyrovnávací paměť, která obsahuje hodnotu pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="788d1-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="788d1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="788d1-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="788d1-114">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="788d1-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="788d1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="788d1-115">Requirements</span></span>  
 <span data-ttu-id="788d1-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="788d1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="788d1-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="788d1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="788d1-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="788d1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="788d1-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="788d1-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788d1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="788d1-120">See Also</span></span>  
 [<span data-ttu-id="788d1-121">ICorDebugVariableSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="788d1-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="788d1-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="788d1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
