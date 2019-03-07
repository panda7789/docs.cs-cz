---
title: ICorDebugInstanceFieldSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2119b1ce43d5969c8d083e955210c69af69b44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491435"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="9014b-102">ICorDebugInstanceFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9014b-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="9014b-103">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="9014b-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9014b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9014b-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9014b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9014b-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="9014b-106">[out] Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="9014b-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9014b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9014b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9014b-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9014b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9014b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9014b-109">Requirements</span></span>  
 <span data-ttu-id="9014b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9014b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9014b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9014b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9014b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9014b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9014b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9014b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9014b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9014b-114">See also</span></span>
- [<span data-ttu-id="9014b-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9014b-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="9014b-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9014b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
