---
title: "ICorDebugSymbolProvider::GetInstanceFieldSymbols – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b40a3656abc6b6d882e7318d46f9dc189a4eb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="744d3-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="744d3-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="744d3-103">Získá instanci symbolů pole, které odpovídají typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="744d3-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="744d3-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="744d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="744d3-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="744d3-106">[v] Počet bajtů `typeSig` pole.</span><span class="sxs-lookup"><span data-stu-id="744d3-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="744d3-107">[v] Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="744d3-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="744d3-108">[v] Počet symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="744d3-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="744d3-109">[out] Ukazatel na počet symboly načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="744d3-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="744d3-110">[out] Ukazatel na [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, které obsahuje pole symboly požadovaný instance.</span><span class="sxs-lookup"><span data-stu-id="744d3-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="744d3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="744d3-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="744d3-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="744d3-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="744d3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="744d3-113">Requirements</span></span>  
 <span data-ttu-id="744d3-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="744d3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744d3-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="744d3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="744d3-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="744d3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="744d3-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744d3-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744d3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="744d3-118">See Also</span></span>  
 [<span data-ttu-id="744d3-119">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="744d3-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)  
 [<span data-ttu-id="744d3-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="744d3-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="744d3-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="744d3-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
