---
title: ICorDebugInstanceFieldSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0901e64a7da7f68b2fbcdb63636503893263435f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413787"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="5c8b2-102">ICorDebugInstanceFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="5c8b2-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="5c8b2-103">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="5c8b2-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c8b2-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c8b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c8b2-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="5c8b2-106">[out] Ukazatel na délka pole.</span><span class="sxs-lookup"><span data-stu-id="5c8b2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c8b2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c8b2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c8b2-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="5c8b2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c8b2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c8b2-109">Requirements</span></span>  
 <span data-ttu-id="5c8b2-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c8b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c8b2-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c8b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c8b2-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c8b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c8b2-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c8b2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8b2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c8b2-114">See Also</span></span>  
 [<span data-ttu-id="5c8b2-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c8b2-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="5c8b2-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5c8b2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
