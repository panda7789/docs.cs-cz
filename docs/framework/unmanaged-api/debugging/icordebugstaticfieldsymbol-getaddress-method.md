---
title: 'ICorDebugStaticFieldSymbol:: GetAddress – metoda'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d41b99d7410333cb6a22443271c1fcbc41c3594
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962704"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="a3424-102">ICorDebugStaticFieldSymbol:: GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="a3424-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="a3424-103">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="a3424-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3424-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3424-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3424-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3424-105">Parameters</span></span>  
 <span data-ttu-id="a3424-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="a3424-106">pRVA</span></span>  
 <span data-ttu-id="a3424-107">mimo Ukazatel na relativní virtuální adresu (RVA) statického pole.</span><span class="sxs-lookup"><span data-stu-id="a3424-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3424-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3424-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3424-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a3424-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3424-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3424-110">Requirements</span></span>  
 <span data-ttu-id="a3424-111">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3424-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3424-112">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3424-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3424-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3424-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3424-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3424-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3424-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3424-115">See also</span></span>

- [<span data-ttu-id="a3424-116">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3424-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="a3424-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a3424-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
