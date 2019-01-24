---
title: ICorDebugStaticFieldSymbol::GetAddress – metoda
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 331f335364542fd299a51d25e54d5b6606d19e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731020"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="14e54-102">ICorDebugStaticFieldSymbol::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="14e54-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="14e54-103">Získá adresu statické pole.</span><span class="sxs-lookup"><span data-stu-id="14e54-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14e54-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14e54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14e54-105">Parameters</span></span>  
 <span data-ttu-id="14e54-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="14e54-106">pRVA</span></span>  
 <span data-ttu-id="14e54-107">[out] Ukazatel na relativní virtuální adresu (RVA) statické pole.</span><span class="sxs-lookup"><span data-stu-id="14e54-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14e54-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14e54-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14e54-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14e54-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14e54-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14e54-110">Requirements</span></span>  
 <span data-ttu-id="14e54-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14e54-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e54-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14e54-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14e54-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14e54-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14e54-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e54-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e54-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14e54-115">See also</span></span>
- [<span data-ttu-id="14e54-116">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14e54-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="14e54-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="14e54-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
