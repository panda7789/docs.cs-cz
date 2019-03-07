---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ad0878daf57c379a5958dbeacddac8510c6eba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476149"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="4b90e-102">ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="4b90e-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="4b90e-103">Získá statické pole symboly, které odpovídají token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="4b90e-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b90e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b90e-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b90e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b90e-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="4b90e-106">[in] Počet bajtů `typeSig` pole.</span><span class="sxs-lookup"><span data-stu-id="4b90e-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="4b90e-107">[in] Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="4b90e-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="4b90e-108">[in] Počet symbolů požadavku.</span><span class="sxs-lookup"><span data-stu-id="4b90e-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4b90e-109">[out] Ukazatel na počet symbolů načíst pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="4b90e-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="4b90e-110">[out] Ukazatel [icordebugstaticfieldsymbol –](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, které obsahuje symboly požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="4b90e-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b90e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b90e-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b90e-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b90e-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b90e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b90e-113">Requirements</span></span>  
 <span data-ttu-id="4b90e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b90e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b90e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b90e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b90e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b90e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b90e-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b90e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b90e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b90e-118">See also</span></span>
- [<span data-ttu-id="4b90e-119">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="4b90e-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="4b90e-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b90e-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4b90e-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4b90e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
