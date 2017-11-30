---
title: "ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a6741adcc30d3dffee79e909db4334db66eb049
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="4366f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="4366f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="4366f-103">Získá symboly statické pole, které odpovídají typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="4366f-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4366f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4366f-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4366f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4366f-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="4366f-106">[v] Počet bajtů `typeSig` pole.</span><span class="sxs-lookup"><span data-stu-id="4366f-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="4366f-107">[v] Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="4366f-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="4366f-108">[v] Počet symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="4366f-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4366f-109">[out] Ukazatel na počet symboly načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="4366f-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="4366f-110">[out] Ukazatel na [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, která obsahuje požadovanou statické pole symboly.</span><span class="sxs-lookup"><span data-stu-id="4366f-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4366f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4366f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4366f-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="4366f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4366f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4366f-113">Requirements</span></span>  
 <span data-ttu-id="4366f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4366f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4366f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4366f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4366f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4366f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4366f-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4366f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4366f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4366f-118">See Also</span></span>  
 [<span data-ttu-id="4366f-119">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="4366f-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [<span data-ttu-id="4366f-120">ICorDebugSymbolProvider rozhraní</span><span class="sxs-lookup"><span data-stu-id="4366f-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="4366f-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="4366f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
