---
title: ICorDebugStaticFieldSymbol::GetName – metoda
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095c84a5cb448803bbfa45e0fad8a494343ca7f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422315"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="8878f-102">ICorDebugStaticFieldSymbol::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="8878f-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="8878f-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="8878f-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8878f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8878f-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8878f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8878f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8878f-106">[v] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8878f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8878f-107">[out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8878f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8878f-108">[out] Pole znaků, který ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="8878f-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8878f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8878f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8878f-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="8878f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8878f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8878f-111">Requirements</span></span>  
 <span data-ttu-id="8878f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8878f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8878f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8878f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8878f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8878f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8878f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8878f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8878f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8878f-116">See Also</span></span>  
 [<span data-ttu-id="8878f-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8878f-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="8878f-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8878f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
