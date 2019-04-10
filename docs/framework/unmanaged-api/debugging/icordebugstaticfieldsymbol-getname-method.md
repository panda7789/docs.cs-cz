---
title: ICorDebugStaticFieldSymbol::GetName – metoda
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5f52999c3f680fbccefe4681f83d473cdb86306
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206483"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="1d7b6-102">ICorDebugStaticFieldSymbol::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="1d7b6-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="1d7b6-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="1d7b6-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d7b6-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d7b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d7b6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1d7b6-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1d7b6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1d7b6-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1d7b6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d7b6-108">[out] Pole znaků, která ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="1d7b6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d7b6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d7b6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d7b6-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1d7b6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d7b6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d7b6-111">Requirements</span></span>  
 <span data-ttu-id="1d7b6-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d7b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d7b6-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d7b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d7b6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d7b6-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1d7b6-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1d7b6-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d7b6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d7b6-116">See also</span></span>

- [<span data-ttu-id="1d7b6-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d7b6-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="1d7b6-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d7b6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
