---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols – metoda
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 908d53acb9130173327149db95d2d6ec9abc3ae7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540842"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="65517-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="65517-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="65517-103">Získá instanci symboly pole, které odpovídají token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="65517-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65517-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65517-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65517-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65517-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="65517-106">[in] Počet bajtů `typeSig` pole.</span><span class="sxs-lookup"><span data-stu-id="65517-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="65517-107">[in] Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="65517-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="65517-108">[in] Počet symbolů požadavku.</span><span class="sxs-lookup"><span data-stu-id="65517-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="65517-109">[out] Ukazatel na počet symbolů načíst pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="65517-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="65517-110">[out] Ukazatel [icordebugstaticfieldsymbol –](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole obsahující pole symboly požadovaná instance.</span><span class="sxs-lookup"><span data-stu-id="65517-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65517-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65517-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65517-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="65517-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65517-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65517-113">Requirements</span></span>  
 <span data-ttu-id="65517-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65517-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65517-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65517-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65517-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65517-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65517-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65517-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65517-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65517-118">See also</span></span>
- [<span data-ttu-id="65517-119">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="65517-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="65517-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65517-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="65517-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="65517-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
