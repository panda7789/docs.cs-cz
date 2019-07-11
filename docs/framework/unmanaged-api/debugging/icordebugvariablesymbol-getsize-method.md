---
title: ICorDebugVariableSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e963e655c933c9191953bb32ba0b73adf0ae86d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774865"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="6daf7-102">ICorDebugVariableSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6daf7-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="6daf7-103">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6daf7-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6daf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6daf7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6daf7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6daf7-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="6daf7-106">Ukazatel 32bitové celé číslo bez znaménka obsahující velikost proměnné.</span><span class="sxs-lookup"><span data-stu-id="6daf7-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6daf7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6daf7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6daf7-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6daf7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6daf7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6daf7-109">Requirements</span></span>  
 <span data-ttu-id="6daf7-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6daf7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6daf7-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6daf7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6daf7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6daf7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6daf7-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6daf7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6daf7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6daf7-114">See also</span></span>

- [<span data-ttu-id="6daf7-115">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6daf7-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="6daf7-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6daf7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
