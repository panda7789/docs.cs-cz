---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols – metoda
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d016007d09a06e923bef78fa8ead99e1e1ce9420
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771368"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="49a9a-102">ICorDebugSymbolProvider::GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="49a9a-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="49a9a-103">Získá symboly parametr metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="49a9a-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49a9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49a9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49a9a-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="49a9a-106">[in] Nativní relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="49a9a-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="49a9a-107">[in] Číslo lokální symboly požadovaný.</span><span class="sxs-lookup"><span data-stu-id="49a9a-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="49a9a-108">[out] Ukazatel na počet symbolů načíst pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="49a9a-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="49a9a-109">[out] Ukazatel [icordebugvariablesymbol –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) pole, které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="49a9a-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49a9a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49a9a-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49a9a-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49a9a-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49a9a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49a9a-112">Requirements</span></span>  
 <span data-ttu-id="49a9a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49a9a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49a9a-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49a9a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49a9a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49a9a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49a9a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49a9a-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a9a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49a9a-117">See also</span></span>

- [<span data-ttu-id="49a9a-118">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="49a9a-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="49a9a-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49a9a-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="49a9a-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="49a9a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
