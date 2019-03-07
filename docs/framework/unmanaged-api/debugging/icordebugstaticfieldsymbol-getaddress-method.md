---
title: ICorDebugStaticFieldSymbol::GetAddress – metoda
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a78df94fdc4190a43c80b0a8e3457f164e38eb00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498052"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="f7dc7-102">ICorDebugStaticFieldSymbol::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="f7dc7-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="f7dc7-103">Získá adresu statické pole.</span><span class="sxs-lookup"><span data-stu-id="f7dc7-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7dc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7dc7-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7dc7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7dc7-105">Parameters</span></span>  
 <span data-ttu-id="f7dc7-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="f7dc7-106">pRVA</span></span>  
 <span data-ttu-id="f7dc7-107">[out] Ukazatel na relativní virtuální adresu (RVA) statické pole.</span><span class="sxs-lookup"><span data-stu-id="f7dc7-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7dc7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7dc7-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7dc7-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f7dc7-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7dc7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7dc7-110">Requirements</span></span>  
 <span data-ttu-id="f7dc7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7dc7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7dc7-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7dc7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7dc7-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7dc7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7dc7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7dc7-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7dc7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7dc7-115">See also</span></span>
- [<span data-ttu-id="f7dc7-116">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7dc7-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f7dc7-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7dc7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
