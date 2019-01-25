---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols – metoda
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be103b8f9d6f94d5b7a265ec2ef01c551622c9e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714292"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="b770e-102">ICorDebugSymbolProvider::GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b770e-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="b770e-103">Získá symboly parametr metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="b770e-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b770e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b770e-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b770e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b770e-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="b770e-106">[in] Nativní relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="b770e-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="b770e-107">[in] Číslo lokální symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="b770e-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="b770e-108">[out] Ukazatel na počet symbolů načíst pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="b770e-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="b770e-109">[out] Ukazatel [icordebugvariablesymbol –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) pole, které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="b770e-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b770e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b770e-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b770e-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b770e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b770e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b770e-112">Requirements</span></span>  
 <span data-ttu-id="b770e-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b770e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b770e-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b770e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b770e-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b770e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b770e-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b770e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b770e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b770e-117">See also</span></span>
- [<span data-ttu-id="b770e-118">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b770e-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="b770e-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b770e-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b770e-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b770e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
