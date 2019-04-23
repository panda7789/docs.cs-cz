---
title: ICorDebugStaticFieldSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9baa3632b6ede9ce45f34302611710344ed33761
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154320"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="4247e-102">ICorDebugStaticFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="4247e-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="4247e-103">Získá velikost v bajtech statické pole.</span><span class="sxs-lookup"><span data-stu-id="4247e-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4247e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4247e-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4247e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4247e-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="4247e-106">[out] Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="4247e-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4247e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4247e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4247e-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4247e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4247e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4247e-109">Requirements</span></span>  
 <span data-ttu-id="4247e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4247e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4247e-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4247e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4247e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4247e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4247e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4247e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4247e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4247e-114">See also</span></span>

- [<span data-ttu-id="4247e-115">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4247e-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="4247e-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4247e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
