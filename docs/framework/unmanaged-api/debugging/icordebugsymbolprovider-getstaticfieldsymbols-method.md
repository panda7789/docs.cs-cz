---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7d5195215762c25b2d7dc2b71fcd53959656303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420892"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="6520b-102">ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="6520b-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="6520b-103">Získá symboly statické pole, které odpovídají typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="6520b-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6520b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6520b-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6520b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6520b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="6520b-106">[v] Počet bajtů `typeSig` pole.</span><span class="sxs-lookup"><span data-stu-id="6520b-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="6520b-107">[v] Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="6520b-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="6520b-108">[v] Počet symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="6520b-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="6520b-109">[out] Ukazatel na počet symboly načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="6520b-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="6520b-110">[out] Ukazatel na [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, která obsahuje požadovanou statické pole symboly.</span><span class="sxs-lookup"><span data-stu-id="6520b-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6520b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6520b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6520b-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="6520b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6520b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6520b-113">Requirements</span></span>  
 <span data-ttu-id="6520b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6520b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6520b-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6520b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6520b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6520b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6520b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6520b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6520b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6520b-118">See Also</span></span>  
 [<span data-ttu-id="6520b-119">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="6520b-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [<span data-ttu-id="6520b-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6520b-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="6520b-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6520b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
