---
title: 'ICorDebugStaticFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: 0fa9c519a40624dd8c5471231263d2430738af87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131772"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="db9b2-102">ICorDebugStaticFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="db9b2-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="db9b2-103">Získá velikost statického pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="db9b2-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db9b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db9b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db9b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db9b2-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="db9b2-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="db9b2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db9b2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db9b2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db9b2-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="db9b2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db9b2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db9b2-109">Requirements</span></span>  
 <span data-ttu-id="db9b2-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db9b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db9b2-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db9b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db9b2-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db9b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db9b2-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db9b2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9b2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db9b2-114">See also</span></span>

- [<span data-ttu-id="db9b2-115">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db9b2-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="db9b2-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="db9b2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
