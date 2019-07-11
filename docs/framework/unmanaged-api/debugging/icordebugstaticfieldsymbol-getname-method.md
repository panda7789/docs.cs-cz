---
title: ICorDebugStaticFieldSymbol::GetName – metoda
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01281e09533ba7196d3fa3e57c463636cfb0dd77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760836"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="f0154-102">ICorDebugStaticFieldSymbol::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="f0154-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="f0154-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="f0154-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0154-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0154-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0154-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0154-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f0154-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f0154-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f0154-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f0154-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f0154-108">[out] Pole znaků, která ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="f0154-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0154-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0154-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0154-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0154-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0154-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0154-111">Requirements</span></span>  
 <span data-ttu-id="f0154-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0154-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0154-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0154-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0154-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0154-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0154-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0154-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0154-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0154-116">See also</span></span>

- [<span data-ttu-id="f0154-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0154-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f0154-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f0154-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
