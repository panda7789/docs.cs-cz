---
title: "ICorDebugVariableSymbol::GetValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 789bca88ea2f2d87ebfc73275b4a7569fcbe8cc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="f6594-102">ICorDebugVariableSymbol::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="f6594-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="f6594-103">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="f6594-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6594-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6594-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f6594-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6594-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="f6594-106">[v] Počáteční odsazení v proměnné z kterého se mají číst hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6594-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="f6594-107">Tento parametr se používá při čtení člen pole v objektu.</span><span class="sxs-lookup"><span data-stu-id="f6594-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="f6594-108">[v] Velikost v bajtech `context` argument.</span><span class="sxs-lookup"><span data-stu-id="f6594-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="f6594-109">[v] Kontext vlákno použít ke čtení hodnota.</span><span class="sxs-lookup"><span data-stu-id="f6594-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="f6594-110">[v] Velikost v bajtech `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f6594-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="f6594-111">[out] Počet bajtů ve skutečnosti zapsána do `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f6594-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f6594-112">[out] Bajtové pole, která obsahuje hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="f6594-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6594-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6594-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6594-114">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="f6594-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6594-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6594-115">Requirements</span></span>  
 <span data-ttu-id="f6594-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6594-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6594-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6594-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6594-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6594-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6594-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6594-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6594-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6594-120">See Also</span></span>  
 [<span data-ttu-id="f6594-121">ICorDebugVariableSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6594-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="f6594-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6594-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
