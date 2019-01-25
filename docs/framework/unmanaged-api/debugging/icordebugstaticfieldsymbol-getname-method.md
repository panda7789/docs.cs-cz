---
title: ICorDebugStaticFieldSymbol::GetName – metoda
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da390fb7de3c248fa5389f133d65f9914d5260a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714688"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="30238-102">ICorDebugStaticFieldSymbol::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="30238-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="30238-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="30238-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30238-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30238-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30238-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="30238-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="30238-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="30238-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="30238-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="30238-108">[out] Pole znaků, která ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="30238-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30238-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30238-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30238-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30238-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30238-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30238-111">Requirements</span></span>  
 <span data-ttu-id="30238-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30238-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30238-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30238-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30238-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30238-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30238-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30238-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30238-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30238-116">See also</span></span>
- [<span data-ttu-id="30238-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30238-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="30238-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="30238-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
