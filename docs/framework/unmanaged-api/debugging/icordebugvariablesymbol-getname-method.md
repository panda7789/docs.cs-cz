---
title: ICorDebugVariableSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aff2686830290e38df3d3a79b2bea6fa0b4a280
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774890"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="f59e2-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="f59e2-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="f59e2-103">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="f59e2-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f59e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f59e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f59e2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f59e2-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f59e2-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f59e2-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f59e2-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f59e2-108">Ukazatel na pole znaků, který obsahuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="f59e2-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f59e2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f59e2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f59e2-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f59e2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f59e2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f59e2-111">Requirements</span></span>  
 <span data-ttu-id="f59e2-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f59e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f59e2-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f59e2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f59e2-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f59e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f59e2-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f59e2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f59e2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f59e2-116">See also</span></span>

- [<span data-ttu-id="f59e2-117">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f59e2-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="f59e2-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f59e2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
