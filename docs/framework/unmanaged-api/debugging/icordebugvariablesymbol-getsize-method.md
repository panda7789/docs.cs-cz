---
title: ICorDebugVariableSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027b3f773ff0ed0ca7bf9d193f97a3b060ea8494
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211839"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="4cfcc-102">ICorDebugVariableSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="4cfcc-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="4cfcc-103">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4cfcc-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cfcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cfcc-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cfcc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cfcc-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="4cfcc-106">Ukazatel 32bitové celé číslo bez znaménka obsahující velikost proměnné.</span><span class="sxs-lookup"><span data-stu-id="4cfcc-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cfcc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cfcc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cfcc-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4cfcc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cfcc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cfcc-109">Requirements</span></span>  
 <span data-ttu-id="4cfcc-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cfcc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cfcc-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cfcc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cfcc-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cfcc-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4cfcc-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4cfcc-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4cfcc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cfcc-114">See also</span></span>

- [<span data-ttu-id="4cfcc-115">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cfcc-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="4cfcc-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cfcc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
