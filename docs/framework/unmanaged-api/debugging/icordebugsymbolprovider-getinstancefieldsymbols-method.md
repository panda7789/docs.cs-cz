---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols – metoda
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b5bb29ffa313df8b2ec3de9d1dca7ddbc99c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422612"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="037a6-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="037a6-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="037a6-103">Získá instanci symbolů pole, které odpovídají typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="037a6-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="037a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="037a6-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="037a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="037a6-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="037a6-106">[v] Počet bajtů `typeSig` pole.</span><span class="sxs-lookup"><span data-stu-id="037a6-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="037a6-107">[v] Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="037a6-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="037a6-108">[v] Počet symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="037a6-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="037a6-109">[out] Ukazatel na počet symboly načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="037a6-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="037a6-110">[out] Ukazatel na [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, které obsahuje pole symboly požadovaný instance.</span><span class="sxs-lookup"><span data-stu-id="037a6-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="037a6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="037a6-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="037a6-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="037a6-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="037a6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="037a6-113">Requirements</span></span>  
 <span data-ttu-id="037a6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="037a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="037a6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="037a6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="037a6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="037a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="037a6-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="037a6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037a6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="037a6-118">See Also</span></span>  
 [<span data-ttu-id="037a6-119">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="037a6-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)  
 [<span data-ttu-id="037a6-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="037a6-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="037a6-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="037a6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
