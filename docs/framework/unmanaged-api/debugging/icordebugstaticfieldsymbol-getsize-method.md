---
title: 'ICorDebugStaticFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d99e06c1093dbc67e9c1999e4b9ccabd6579340e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962665"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="f5440-102">ICorDebugStaticFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="f5440-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="f5440-103">Získá velikost statického pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f5440-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5440-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5440-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5440-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5440-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="f5440-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="f5440-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5440-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5440-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5440-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f5440-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5440-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5440-109">Requirements</span></span>  
 <span data-ttu-id="f5440-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5440-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5440-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5440-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5440-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5440-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5440-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5440-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5440-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5440-114">See also</span></span>

- [<span data-ttu-id="f5440-115">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5440-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f5440-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f5440-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
