---
title: ICorDebugInstanceFieldSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc09de2120399dcfe309757d554e1de72e55f07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081447"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="0f5f3-102">ICorDebugInstanceFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0f5f3-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="0f5f3-103">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="0f5f3-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f5f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f5f3-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f5f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f5f3-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="0f5f3-106">[out] Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="0f5f3-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f5f3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f5f3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f5f3-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0f5f3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f5f3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f5f3-109">Requirements</span></span>  
 <span data-ttu-id="0f5f3-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f5f3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f5f3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f5f3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f5f3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f5f3-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0f5f3-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0f5f3-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0f5f3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f5f3-114">See also</span></span>

- [<span data-ttu-id="0f5f3-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f5f3-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="0f5f3-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f5f3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
