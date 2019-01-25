---
title: ICorDebugStaticFieldSymbol::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee8c8a2f88dced7b26d91c17102c42b4338d66ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679302"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="f750c-102">ICorDebugStaticFieldSymbol::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="f750c-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="f750c-103">Získá velikost v bajtech statické pole.</span><span class="sxs-lookup"><span data-stu-id="f750c-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f750c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f750c-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f750c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f750c-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="f750c-106">[out] Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="f750c-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f750c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f750c-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f750c-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f750c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f750c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f750c-109">Requirements</span></span>  
 <span data-ttu-id="f750c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f750c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f750c-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f750c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f750c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f750c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f750c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f750c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f750c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f750c-114">See also</span></span>
- [<span data-ttu-id="f750c-115">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f750c-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f750c-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f750c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
