---
title: "ICorDebugSymbolProvider::GetMethodLocalSymbols – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07151c4cdd43df17025deff4af37a0156ecaf78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="95d28-102">ICorDebugSymbolProvider::GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="95d28-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="95d28-103">Získá symboly místní metoda zadaný relativní virtuální adresa (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="95d28-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95d28-104">Syntax</span></span>  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95d28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95d28-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="95d28-106">[v] Nativní relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="95d28-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="95d28-107">[v] Počet lokální symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="95d28-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="95d28-108">[out] Ukazatel na počet symboly načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="95d28-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="95d28-109">[out] Ukazatel na [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) pole, které obsahuje metody lokální symboly.</span><span class="sxs-lookup"><span data-stu-id="95d28-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95d28-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95d28-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95d28-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="95d28-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95d28-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95d28-112">Requirements</span></span>  
 <span data-ttu-id="95d28-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95d28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d28-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95d28-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95d28-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95d28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95d28-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95d28-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d28-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="95d28-117">See Also</span></span>  
 [<span data-ttu-id="95d28-118">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="95d28-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)  
 [<span data-ttu-id="95d28-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95d28-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="95d28-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="95d28-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
