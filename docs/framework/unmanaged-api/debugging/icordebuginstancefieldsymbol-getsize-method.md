---
title: ICorDebugInstanceFieldSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04d866888c15585ff5058f870257b317ac888be7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696981"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="799cb-102">ICorDebugInstanceFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="799cb-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="799cb-103">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="799cb-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="799cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="799cb-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="799cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="799cb-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="799cb-106">[out] Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="799cb-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="799cb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="799cb-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="799cb-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="799cb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="799cb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="799cb-109">Requirements</span></span>  
 <span data-ttu-id="799cb-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="799cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="799cb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="799cb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="799cb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="799cb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="799cb-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="799cb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799cb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="799cb-114">See also</span></span>
- [<span data-ttu-id="799cb-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="799cb-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="799cb-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="799cb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
