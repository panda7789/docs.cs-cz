---
title: ICorDebugVariableSymbol::GetValue – metoda
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186d9eec0aa6ad9e327b1dd4d0f19e251c79ecf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946182"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="8d6de-102">ICorDebugVariableSymbol::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="8d6de-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="8d6de-103">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="8d6de-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d6de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d6de-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d6de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d6de-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="8d6de-106">[in] Počáteční posun v proměnné, ze kterého se má načíst hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d6de-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="8d6de-107">Tento parametr se používá při čtení pole člena v objektu.</span><span class="sxs-lookup"><span data-stu-id="8d6de-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="8d6de-108">[in] Velikost v bajtech `context` argument.</span><span class="sxs-lookup"><span data-stu-id="8d6de-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="8d6de-109">[in] Kontext vlákna použít ke čtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8d6de-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="8d6de-110">[in] Velikost v bajtech `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8d6de-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="8d6de-111">[out] Počet bajtů zapsaný ve skutečnosti na `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8d6de-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8d6de-112">[out] Bajtové pole obsahující hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="8d6de-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d6de-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d6de-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d6de-114">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d6de-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d6de-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d6de-115">Requirements</span></span>  
 <span data-ttu-id="8d6de-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d6de-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d6de-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d6de-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d6de-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d6de-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d6de-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d6de-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6de-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d6de-120">See also</span></span>

- [<span data-ttu-id="8d6de-121">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d6de-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="8d6de-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8d6de-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
