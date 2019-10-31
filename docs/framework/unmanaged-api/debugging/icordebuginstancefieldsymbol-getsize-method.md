---
title: 'ICorDebugInstanceFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 71828cd8486e2ff09190d23473dbab303b92f933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139020"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="fac85-102">ICorDebugInstanceFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="fac85-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="fac85-103">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="fac85-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fac85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fac85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fac85-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="fac85-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="fac85-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fac85-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fac85-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fac85-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fac85-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fac85-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fac85-109">Requirements</span></span>  
 <span data-ttu-id="fac85-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fac85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac85-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fac85-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fac85-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fac85-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fac85-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fac85-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac85-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fac85-114">See also</span></span>

- [<span data-ttu-id="fac85-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fac85-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="fac85-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fac85-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
