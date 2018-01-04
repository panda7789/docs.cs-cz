---
title: "ICorDebugSymbolProvider::GetMethodParameterSymbols – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd3fc08eec9066f54d90fbe4824ce3f1a1c901dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="57bb5-102">ICorDebugSymbolProvider::GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="57bb5-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="57bb5-103">Získá symboly metoda parametr zadaný relativní virtuální adresa (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="57bb5-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57bb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57bb5-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57bb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57bb5-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="57bb5-106">[v] Nativní relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="57bb5-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="57bb5-107">[v] Počet lokální symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="57bb5-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="57bb5-108">[out] Ukazatel na počet symboly načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="57bb5-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="57bb5-109">[out] Ukazatel na [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) pole, které obsahuje metody lokální symboly.</span><span class="sxs-lookup"><span data-stu-id="57bb5-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57bb5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57bb5-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57bb5-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="57bb5-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57bb5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57bb5-112">Requirements</span></span>  
 <span data-ttu-id="57bb5-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57bb5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57bb5-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57bb5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57bb5-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57bb5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57bb5-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57bb5-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bb5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="57bb5-117">See Also</span></span>  
 [<span data-ttu-id="57bb5-118">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="57bb5-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)  
 [<span data-ttu-id="57bb5-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57bb5-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="57bb5-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="57bb5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
