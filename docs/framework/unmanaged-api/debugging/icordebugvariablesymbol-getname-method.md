---
title: ICorDebugVariableSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d01f8c3956298daee9f11c912406079d98964225
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465295"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="61e0d-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="61e0d-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="61e0d-103">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="61e0d-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61e0d-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61e0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61e0d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="61e0d-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="61e0d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="61e0d-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="61e0d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="61e0d-108">Ukazatel na pole znaků, který obsahuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="61e0d-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61e0d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61e0d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61e0d-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="61e0d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e0d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61e0d-111">Requirements</span></span>  
 <span data-ttu-id="61e0d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61e0d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61e0d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61e0d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61e0d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61e0d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61e0d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61e0d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e0d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61e0d-116">See also</span></span>
- [<span data-ttu-id="61e0d-117">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61e0d-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="61e0d-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="61e0d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
