---
title: 'ICorDebugStaticFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: deeb887dad38417e3ebb980f5ef2f89392388d65
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791811"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="144e0-102">ICorDebugStaticFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="144e0-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="144e0-103">Získá velikost statického pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="144e0-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="144e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="144e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="144e0-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="144e0-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="144e0-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="144e0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="144e0-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="144e0-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="144e0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144e0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="144e0-109">Requirements</span></span>  
 <span data-ttu-id="144e0-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144e0-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="144e0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="144e0-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="144e0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="144e0-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144e0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144e0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="144e0-114">See also</span></span>

- [<span data-ttu-id="144e0-115">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="144e0-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="144e0-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="144e0-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
