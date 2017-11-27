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
ms.openlocfilehash: 364144dcef21e7e9c058cb0317970a273aa8ecac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="bad02-102">ICorDebugInstanceFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="bad02-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="bad02-103">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="bad02-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bad02-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bad02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bad02-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="bad02-106">[out] Ukazatel na délka pole.</span><span class="sxs-lookup"><span data-stu-id="bad02-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bad02-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bad02-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bad02-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="bad02-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad02-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bad02-109">Requirements</span></span>  
 <span data-ttu-id="bad02-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad02-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad02-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bad02-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bad02-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bad02-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bad02-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad02-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad02-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bad02-114">See Also</span></span>  
 [<span data-ttu-id="bad02-115">ICorDebugInstanceFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="bad02-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="bad02-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="bad02-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
