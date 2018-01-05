---
title: "ICorDebugInstanceFieldSymbol::GetSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad13dbe8148d4d9507c6a450d2833da049e0e13a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="d58e9-102">ICorDebugInstanceFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d58e9-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="d58e9-103">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="d58e9-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d58e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d58e9-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d58e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d58e9-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="d58e9-106">[out] Ukazatel na délka pole.</span><span class="sxs-lookup"><span data-stu-id="d58e9-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d58e9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d58e9-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d58e9-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="d58e9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d58e9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d58e9-109">Requirements</span></span>  
 <span data-ttu-id="d58e9-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d58e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d58e9-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d58e9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d58e9-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d58e9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d58e9-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d58e9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58e9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d58e9-114">See Also</span></span>  
 [<span data-ttu-id="d58e9-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d58e9-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="d58e9-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d58e9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
