---
title: ICorDebugVariableSymbol::SetValue – metoda
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b83efca5a8b175d5dc83c03de473262ca033354c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491305"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="6a099-102">ICorDebugVariableSymbol::SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="6a099-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="6a099-103">Přiřadí hodnotu pole bajtů na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6a099-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a099-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a099-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6a099-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a099-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="6a099-106">[in] Počáteční posun v proměnné, ve kterém se má nastavit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6a099-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="6a099-107">Tento parametr se používá při zápisu do pole člena v objektu.</span><span class="sxs-lookup"><span data-stu-id="6a099-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="6a099-108">[in] Identifikátor vlákna, jehož kontext musí být aktualizovány tak, aby odrážely novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6a099-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="6a099-109">[in] Velikost v bajtech kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="6a099-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="6a099-110">[in] Kontext vlákna používá pro zápis hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6a099-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="6a099-111">[in] Velikost v bajtech `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6a099-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="6a099-112">[in] Vyrovnávací paměť, která obsahuje hodnotu pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="6a099-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a099-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a099-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a099-114">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6a099-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a099-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a099-115">Requirements</span></span>  
 <span data-ttu-id="6a099-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a099-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a099-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a099-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a099-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a099-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a099-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a099-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a099-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a099-120">See also</span></span>
- [<span data-ttu-id="6a099-121">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a099-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="6a099-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6a099-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
