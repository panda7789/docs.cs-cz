---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols – metoda
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40123eff4028c1ebda898db27a5bd746571ba7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771404"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="9325f-102">ICorDebugSymbolProvider::GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="9325f-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="9325f-103">Získá místní symboly metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="9325f-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9325f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9325f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9325f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9325f-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="9325f-106">[in] Nativní relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="9325f-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="9325f-107">[in] Číslo lokální symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="9325f-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="9325f-108">[out] Ukazatel na počet symbolů načíst pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="9325f-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="9325f-109">[out] Ukazatel [icordebugvariablesymbol –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) pole, které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="9325f-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9325f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9325f-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9325f-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9325f-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9325f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9325f-112">Requirements</span></span>  
 <span data-ttu-id="9325f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9325f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9325f-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9325f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9325f-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9325f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9325f-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9325f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9325f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9325f-117">See also</span></span>

- [<span data-ttu-id="9325f-118">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="9325f-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="9325f-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9325f-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9325f-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9325f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
