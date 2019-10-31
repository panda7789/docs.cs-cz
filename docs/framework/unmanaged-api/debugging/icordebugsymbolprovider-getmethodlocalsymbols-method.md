---
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 6cd04ea7f83fb7ae96d9ffd1beba39530511ec25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138895"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="7c16c-102">ICorDebugSymbolProvider:: GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="7c16c-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="7c16c-103">Načte místní symboly metody s relativní virtuální adresou (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="7c16c-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c16c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c16c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c16c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c16c-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="7c16c-106">pro Nativní relativní virtuální adresa metody</span><span class="sxs-lookup"><span data-stu-id="7c16c-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="7c16c-107">pro Počet požadovaných místních symbolů.</span><span class="sxs-lookup"><span data-stu-id="7c16c-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="7c16c-108">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="7c16c-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="7c16c-109">mimo Ukazatel na pole [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) , které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="7c16c-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c16c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c16c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c16c-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7c16c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c16c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c16c-112">Requirements</span></span>  
 <span data-ttu-id="7c16c-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c16c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c16c-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c16c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c16c-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c16c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c16c-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c16c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c16c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c16c-117">See also</span></span>

- [<span data-ttu-id="7c16c-118">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="7c16c-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="7c16c-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c16c-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7c16c-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7c16c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
