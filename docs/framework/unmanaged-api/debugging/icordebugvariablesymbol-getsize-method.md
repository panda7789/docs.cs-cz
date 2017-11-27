---
title: "ICorDebugVariableSymbol::GetSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="65c9c-102">ICorDebugVariableSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="65c9c-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="65c9c-103">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="65c9c-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c9c-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65c9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65c9c-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="65c9c-106">Ukazatel 32bitové celé číslo bez znaménka obsahující velikost proměnné.</span><span class="sxs-lookup"><span data-stu-id="65c9c-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65c9c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65c9c-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65c9c-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="65c9c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c9c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65c9c-109">Requirements</span></span>  
 <span data-ttu-id="65c9c-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c9c-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65c9c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65c9c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65c9c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65c9c-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c9c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c9c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="65c9c-114">See Also</span></span>  
 [<span data-ttu-id="65c9c-115">ICorDebugVariableSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c9c-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="65c9c-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c9c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
