---
title: ICorDebugVariableSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01349b6418008db51c432d5c49f8491a44ab60d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419402"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="b84c4-102">ICorDebugVariableSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b84c4-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="b84c4-103">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b84c4-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b84c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b84c4-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b84c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b84c4-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="b84c4-106">Ukazatel 32bitové celé číslo bez znaménka obsahující velikost proměnné.</span><span class="sxs-lookup"><span data-stu-id="b84c4-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b84c4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b84c4-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b84c4-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="b84c4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b84c4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b84c4-109">Requirements</span></span>  
 <span data-ttu-id="b84c4-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b84c4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b84c4-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b84c4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b84c4-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b84c4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b84c4-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b84c4-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84c4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b84c4-114">See Also</span></span>  
 [<span data-ttu-id="b84c4-115">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b84c4-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="b84c4-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b84c4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
